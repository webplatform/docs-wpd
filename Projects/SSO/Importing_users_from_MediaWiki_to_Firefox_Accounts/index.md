---
title: Importing users from MediaWiki to Firefox Accounts
uri: 'WPD:Projects/SSO/Importing users from MediaWiki to Firefox Accounts'

---
This page describes how to query MediaWiki database and run an import script to create accounts within our fork ([WPD:Projects/SSO/Adapt\_Firefox\_Accounts\_for\_WebPlatform](/WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform)) of Firefox Accounts ("FxA").

To have an higher level description of how we implemented it, see [WPD:Projects/SSO/How\_we\_implemented\_it](/WPD:Projects/SSO/How_we_implemented_it).

See canonical version in this [gist.github.com/WebPlatformDocs](https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc)

# Process

-   Requires NodeJS, NPM
-   Clone [fxa-auth-server](https://github.com/webplatform/fxa-auth-server) in a folder of the same name
-   Install dependencies in fxa-auth-server with `npm install`
-   Go a folder up, create a new one and paste the following in it

## 1. Export MediaWiki Users

See also [REAMDE in original gist](https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-mediawiki_sql_query-md)

-   Run this query from MySQL Workbench.

``` html
    SELECT
      CONVERT(user_name USING utf8),
      CONVERT(user_real_name USING utf8),
      CONVERT(user_email USING utf8),
      CONVERT(user_registration, DATETIME),
      user_id
    FROM
      user
    ORDER BY user_id
    LIMIT 40000;
```

-   Export the result in a file \`users.csv\`, it’ll be used to import
-   Make sure the output is a CSV file
    -   one entry per line
    -   Fields in this order: username, realname, email, creation date

Should look like...

``` html
WikiSysop,,team-webplatform-admin@w3.org,"2012-05-29 17:37:32"
NoEmailUser,"Eliot Graff",,"2012-06-26 00:17:47"
```

## 2. Create file run.js

See also [run.js in original gist](https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-run-js)

``` html
/**
 * Import MediaWiki accounts file to run
 *
 * To use within fxa-auth-server deployment.
 *
 * Based on work pushed in https://github.com/mozilla/fxa-auth-server/pull/711
 *
 * See documentation at http://docs.webplatform.org/wiki/WPD:Projects/SSO/Importing_users_from_MediaWiki_to_Firefox_Accounts
 *
 * @author David Kirstein <frozenice@frozenice.de> (http://webplatform.org)
 * @author Renoir Boulanger <renoir@w3.org>
 */

var fs = require('fs');
var Q = require('q');
var csv = require('csv-streamify');
var sleep = require('sleep');
var AccountCreator = require('./accountscreator');

function doSomethingWithLine(line) {
    try {
      var payload = new AccountCreator(line);
    } catch (err) {
      return Q.reject(err);
    }

    return payload.makePromiseToCreate();
}

var fstream = fs.createReadStream('users.csv');
var csvOptions = { empty: null, objectMode: true };
var parser = csv(csvOptions);
var workItems = [], errors = [];

parser.on('readable', function() {
  var line = parser.read(); // line is an array of fields
  sleep.usleep(100 * 1000); // sleep 100 ms
  var promise = doSomethingWithLine(line);
  promise.done(function onFulfilled() {
    // Nothing
  }, function onRejected(a) {
    errors.push([line[0], a.message || a]);
  });
  workItems.push(promise);
});

fstream.pipe(parser).on('end', function() {
  waitForAllPromises();
});

function waitForAllPromises() {
  // use allSettled, all would abort if just one promise would be rejected
  Q.allSettled(workItems).done(function() {
    console.log('all done! errors:');
    console.error(errors);
  });
}
```

## 3. Create file accountscreator.js

See also [accountscreator.js in original gist](https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-accountscreator-js)

``` html
/**
 * Import MediaWiki accounts
 *
 * To use within fxa-auth-server deployment.
 *
 * Based on work pushed in https://github.com/mozilla/fxa-auth-server/pull/711
 *
 * See documentation at http://docs.webplatform.org/wiki/WPD:Projects/SSO/Importing_users_from_MediaWiki_to_Firefox_Accounts
 *
 * @author Renoir Boulanger <renoir@w3.org>
 */

// Password (DO NOT USE THE SAME AS POSTED ONLINE!1)
var password = '4e9bde2d85';

    /**
     * fxa-auth-server listen IP and port
     *
     * Make sure it matches the same configuration
     * otherwise the hashing validation will fail with
     * "Bad mac" error message.
     *
     * See config/config.js in listen section.
     *
     * @type {String} FXA Auth server HTTP endpoint to make calls against
     */
var  instanceEndpoint = 'https://api.accounts.webplatform.org';

var fs = require('fs'),
    publicKey = JSON.parse(fs.readFileSync('../fxa-auth-server/config/public-key.json')),
    Client = require('../fxa-auth-server/client'),
    duration = 1000 * 60 * 60 * 24,
    client = null;

function AccountCreator(dataObject) {
  if ( dataObject[2] === null ) {
    throw 'User MUST have an email address for ' + dataObject[0];
  }
  // Use a hard to guess password to force users to ask a new one
  this.password = password;
  this.email = dataObject[2]; // See _parseUserData
  this.config = {pk: publicKey, d: duration, ep: instanceEndpoint};
  this.userData = this._parseUserData(dataObject);
}

/**
 * Format options array for overloaded signup
 *
 * userData expects 4 members:
 * - MediaWiki username
 * - Full name
 * - Email address
 * - Registration date
 *
 * @param  array  userData      data in a predetermined order
 * @return object optionsObject what we return as 3rd argument to ClientCreate call
 */
AccountCreator.prototype._parseUserData = function _parseUserData(userData) {
    var dateObject = new Date(userData[3]),
        out = {};

    out.preVerified = true;
    out.username = userData[0];
    out.fullName = userData[1] || null;
    out.forceCreatedAt = dateObject.getTime();

    return out;
};

AccountCreator.prototype.makePromiseToCreate = function makePromiseToCreate () {
  return Client.create(this.config.ep, this.email, this.password, this.userData)
          .then(function(a){
            console.log('Created ', a.email);
          });
};

module.exports = AccountCreator;
```

## 4. Create a new package.json

See original [package.json gist](https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-package-json)

``` html
{
  "name": "mediawiki-to-fxa-user-importer",
  "version": "0.0.1",
  "dependencies": {
    "q": "~1.0.0",
    "csv-streamify":"~1.0.0",
    "sleep": "~1.1.5"
  }
}
```

 Run

``` html
npm install
```

## 5. Run import script

Note that this step can take some time. With \~39 000 users, it took a bit more than an hour to run in full.

``` html
node run.js
```
