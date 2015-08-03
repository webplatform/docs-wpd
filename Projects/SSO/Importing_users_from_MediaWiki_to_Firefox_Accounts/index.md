---
title: WPD:Projects/SSO/Importing users from MediaWiki to Firefox Accounts
---
<h1><span class="mw-headline" id="Importing_users_from_MediaWiki_to_Firefox_Accounts">Importing users from MediaWiki to Firefox Accounts</span></h1>
<p>This page describes how to query MediaWiki database and run an import script to create accounts within our fork (<a href="/wiki/WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform" title="WPD:Projects/SSO/Adapt Firefox Accounts for WebPlatform">WPD:Projects/SSO/Adapt_Firefox_Accounts_for_WebPlatform</a>) of Firefox Accounts ("FxA").
</p><p>To have an higher level description of how we implemented it, see <a href="/wiki/WPD:Projects/SSO/How_we_implemented_it" title="WPD:Projects/SSO/How we implemented it">WPD:Projects/SSO/How_we_implemented_it</a>.
</p><p>See canonical version in this <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc">gist.github.com/WebPlatformDocs</a>
</p>
<h1><span class="mw-headline" id="Process">Process</span></h1>
<ul><li> Requires NodeJS, NPM</li>
<li> Clone <a rel="nofollow" class="external text" href="https://github.com/webplatform/fxa-auth-server">fxa-auth-server</a> in a folder of the same name</li>
<li> Install dependencies in fxa-auth-server with <tt>npm install</tt></li>
<li> Go a folder up, create a new one and paste the following in it</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="1._Export_MediaWiki_Users">1. Export MediaWiki Users</span></h2>
<p>See also <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-mediawiki_sql_query-md">REAMDE in original gist</a>
</p>
<ul><li> Run this query from MySQL Workbench.</li></ul>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">    SELECT
      CONVERT(user_name USING utf8),
      CONVERT(user_real_name USING utf8),
      CONVERT(user_email USING utf8),
      CONVERT(user_registration, DATETIME),
      user_id
    FROM
      user
    ORDER BY user_id
    LIMIT 40000;</pre></div></div>
<ul><li> Export the result in a file `users.csv`, it’ll be used to import</li>
<li> Make sure the output is a CSV file 
<ul><li> one entry per line</li>
<li> Fields in this order:  username, realname, email, creation date</li></ul></li></ul>
<p>Should look like...
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">WikiSysop,,team-webplatform-admin@w3.org,&quot;2012-05-29 17:37:32&quot;
NoEmailUser,&quot;Eliot Graff&quot;,,&quot;2012-06-26 00:17:47&quot;</pre></div></div>
<h2><span class="mw-headline" id="2._Create_file_run.js">2. Create file run.js</span></h2>
<p>See also <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-run-js">run.js in original gist</a>
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">/**
 * Import MediaWiki accounts file to run
 *
 * To use within fxa-auth-server deployment.
 *
 * Based on work pushed in https://github.com/mozilla/fxa-auth-server/pull/711
 *
 * See documentation at http://docs.webplatform.org/wiki/WPD:Projects/SSO/Importing_users_from_MediaWiki_to_Firefox_Accounts
 *
 * @author David Kirstein <span class="sc2">&lt;frozenice@frozenice.de&gt;</span> (http://webplatform.org)
 * @author Renoir Boulanger <span class="sc2">&lt;renoir@w3.org&gt;</span>
 */
&#160;
var fs = require('fs');
var Q = require('q');
var csv = require('csv-streamify');
var sleep = require('sleep');
var AccountCreator = require('./accountscreator');
&#160;
function doSomethingWithLine(line) {
    try {
      var payload = new AccountCreator(line);
    } catch (err) {
      return Q.reject(err);
    }
&#160;
    return payload.makePromiseToCreate();
}
&#160;
var fstream = fs.createReadStream('users.csv');
var csvOptions = { empty: null, objectMode: true };
var parser = csv(csvOptions);
var workItems = [], errors = [];
&#160;
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
&#160;
fstream.pipe(parser).on('end', function() {
  waitForAllPromises();
});
&#160;
function waitForAllPromises() {
  // use allSettled, all would abort if just one promise would be rejected
  Q.allSettled(workItems).done(function() {
    console.log('all done! errors:');
    console.error(errors);
  });
}</pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="3._Create_file_accountscreator.js">3. Create file accountscreator.js</span></h2>
<p>See also <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-accountscreator-js">accountscreator.js in original gist</a>
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">/**
 * Import MediaWiki accounts
 *
 * To use within fxa-auth-server deployment.
 *
 * Based on work pushed in https://github.com/mozilla/fxa-auth-server/pull/711
 *
 * See documentation at http://docs.webplatform.org/wiki/WPD:Projects/SSO/Importing_users_from_MediaWiki_to_Firefox_Accounts
 * 
 * @author Renoir Boulanger <span class="sc2">&lt;renoir@w3.org&gt;</span>
 */
&#160;
// Password (DO NOT USE THE SAME AS POSTED ONLINE!1)
var password = '4e9bde2d85';
&#160;
    /**
     * fxa-auth-server listen IP and port
     *
     * Make sure it matches the same configuration
     * otherwise the hashing validation will fail with
     * &quot;Bad mac&quot; error message.
     *
     * See config/config.js in listen section.
     *
     * @type {String} FXA Auth server HTTP endpoint to make calls against
     */
var  instanceEndpoint = 'https://api.accounts.webplatform.org';
&#160;
var fs = require('fs'),
    publicKey = JSON.parse(fs.readFileSync('../fxa-auth-server/config/public-key.json')),
    Client = require('../fxa-auth-server/client'),
    duration = 1000 * 60 * 60 * 24,
    client = null;
&#160;
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
&#160;
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
&#160;
    out.preVerified = true;
    out.username = userData[0];
    out.fullName = userData[1] || null;
    out.forceCreatedAt = dateObject.getTime();
&#160;
    return out;
};
&#160;
AccountCreator.prototype.makePromiseToCreate = function makePromiseToCreate () {
  return Client.create(this.config.ep, this.email, this.password, this.userData)
          .then(function(a){
            console.log('Created ', a.email);
          });
};
&#160;
module.exports = AccountCreator;</pre></div></div>
<h2><span class="mw-headline" id="4._Create_a_new_package.json">4. Create a new package.json</span></h2>
<p>See original <a rel="nofollow" class="external text" href="https://gist.github.com/WebPlatformDocs/5543e6314dde476283fc#file-package-json">package.json gist</a>
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{
  &quot;name&quot;: &quot;mediawiki-to-fxa-user-importer&quot;,
  &quot;version&quot;: &quot;0.0.1&quot;,
  &quot;dependencies&quot;: {
    &quot;q&quot;: &quot;~1.0.0&quot;,
    &quot;csv-streamify&quot;:&quot;~1.0.0&quot;,
    &quot;sleep&quot;: &quot;~1.1.5&quot;
  }
}</pre></div></div>
<p>Run 
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">npm install</pre></div></div>
<p><br />
</p>
<h2><span class="mw-headline" id="5._Run_import_script">5. Run import script</span></h2>
<p>Note that this step can take some time. With ~39 000 users, it took a bit more than an hour to run in full.
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">node run.js</pre></div></div>

<!-- 
NewPP limit report
CPU time usage: 0.061 seconds
Real time usage: 0.063 seconds
Preprocessor visited node count: 83/1000000
Preprocessor generated node count: 172/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:23275-0!*!0!!*!*!*!esi=1 and timestamp 20150731071432 and revision id 56281
 -->
