---
title: Installing Firefox Accounts ("FxA")
uri: 'WPD:Infrastructure/procedures/Installing and theme Firefox accounts'

---
Canonical version [published in this gist](https://gist.github.com/renoirb/81a3544bce3a5831e793)

Procedure to install [Firefox Accounts system](https://wiki.mozilla.org/Identity/Firefox_Accounts) to [WebPlatform](http://www.webplatform.org/) infrastructure.

It requires a set of components:

-   [Firefox Accounts Content server](https://github.com/mozilla/fxa-content-server) that holds the HTML/CSS/JavaScript files for the frontend
-   [Firefox Accounts Authentication server](https://github.com/mozilla/fxa-auth-server)
-   [Firefox Accounts Profile server](https://github.com/mozilla/fxa-profile-server)
-   [Firefox Accounts OAuth server](https://github.com/mozilla/fxa-oauth-server)

# <span>Misc notes</span>

-   <https://github.com/mozilla/fxa-oauth-server>
-   <https://github.com/mozilla/fxa-oauth-server/wiki/oauth-design>

## <span>OAuth terminology regarding grants/roles/entitlement</span>

> seanmonstar: ... the oauth spec uses "grant" where we use "code". OAuth server sends a code to app, and the app trades the "code" for a token.

# <span>Procedure</span>

## <span>Install Firefox Content server</span>

Basic system utilities

    sudo apt-get install nginx-full git nodejs npm

Ubuntu package-names collision fix, we want nodejs, not radio amateur utility.

    sudo ln -s /usr/bin/nodejs /usr/bin/node

Deployment specific requirements:

    sudo apt-get install libgmp-dev libgmp10
    sudo npm install -g grunt-cli phantomjs bower bunyan forever

Creating folder:

    sudo mkdir -p /srv/webplatform/auth/fxa-content-server
    sudo chown -R ubuntu:ubuntu /srv/webplatform

Project dependencies

    cd /srv/webplatform/auth/fxa-content-server
    git clone https://github.com/mozilla/fxa-content-server.git .

Checkout the latest `train-X` they have available. Both auth and content projects should have matching branches.

    git branch -r
    git checkout -t origin/train-11

Install dependencies

    npm install
    bower install

Available configuration options, through Convict

    cp server/config/local.json-dist server/config/local.json

Note that the `local.json` is in the gitignore and is used by default so you do not need to set command line argument to specify which configuration file to load.

**Configuration**, refer to [fxa-content-server](https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-content-server) config block below.

Note that you can see available options the project base Convict file.

    more server/lib/configuration.js

Configuration notes:

-   `fxaccount_url`: Is where you will expose the *fxa-auth-server*, ideally through a HTTP server that has a valid SSL certificate, in our case `api.accounts.webplatform.org`

Start the service:

    grunt server:dist

This command will take care to compile all assets into static ones, and make a local HTTP server so we can use NGINX to forward to it.

*Process runner:* Ideally this should be ran through a process runner (forever) and logs should be sent to a logger. \#TODO

*NOTE* It has been validated with `zaach` that content-server requires nodejs. Therefore we cannot just use an HTTP server to serve file, they are not fully static.

## <span>Install Firefox Account Authentication service</span>

Clone the project

    cd /srv/webplatform/auth
    git clone git://github.com/mozilla/fxa-auth-server.git
    cd fxa-auth-server

Checkout the latest `train-X` they have available.

    git branch -r
    git checkout -t origin/train-10

Install dependencies

    npm install

**Configuration**, refer to [fxa-auth-server](https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-auth-server) config block below.

Note that you can see available options the project base Convict file.

    more config/config.js

The file name can match the environment name. For example, if you use `NODE_ENV=prod`, the file would be `config/prod.json`

Notes about the keys:

-   `contentServer`: Is the URL where the *fxa-content-server* is
-   `templateServer`: Is, also, where the *fxa-content-server* is (in case you want a different address)

## <span>Install OAuth service</span>

Clone the project

    cd /srv/webplatform/auth
    git clone git://github.com/mozilla/fxa-oauth-server.git
    cd fxa-oauth-server
    git checkout -t origin/master

Install dependencies

    npm install

**Configuration**, refer to [fxa-oauth-server](https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-oauth-server) config block below.

You can see the available configuration switches here:

    more lib/config.js
    more config/dev.json

Note that the `clients` array will ensure that the services are inserted in the database. This is how you allow a service to authenticate against the service.

Note also the `whitelisted`, this property is useful to differentiate services that we want to pass through OAuth without asking each user to confirm the use. To learn more about generating keys, you can see it in the [fxa-oauth-server/doc/clients.md](https://github.com/mozilla/fxa-oauth-server/blob/master/docs/clients.md)

## <span>Configure NGINX</span>

Note, we are creating self-signed for the moment.

    sudo -s
    cd /etc/nginx/ssl

From here, you have two choices:

-   Install your key and certificates
-   Create self-signed certificates

It is expected that you have the following files in `/etc/nginx/ssl`

Adjust vhost:

    vi /etc/nginx/sites-enabled/accounts

Paste:

    server {
        listen      80;
        server_name accounts.webplatform.org;
        return      301 https://accounts.webplatform.org$request_uri;
    }

    server {
        listen      80;
        server_name api.accounts.webplatform.org;
        return      301 https://api.accounts.webplatform.org$request_uri;
    }

    server {
        listen      80;
        server_name oauth.accounts.webplatform.org;
        return      301 https://oauth.accounts.webplatform.org$request_uri;
    }

    server {
        listen       443 ssl;
        server_name  accounts.webplatform.org;

        location / {
          proxy_pass http://127.0.0.1:3030;
        }

        ssl on;
        ssl_certificate     ssl/accounts.webplatform-20140401.pem;
        ssl_certificate_key ssl/201404.key;
        ssl_session_timeout 5m;
        ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers "HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES";
        ssl_prefer_server_ciphers on;
    }

    server {
        listen       443 ssl;
        server_name  api.accounts.webplatform.org;

        location / {
          proxy_pass http://127.0.0.1:9000;
        }

        ssl on;
        ssl_certificate     ssl/api.accounts.webplatform-20140401.pem;
        ssl_certificate_key ssl/201404.key;
        ssl_session_timeout 5m;
        ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers "HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES";
        ssl_prefer_server_ciphers on;
    }

    server {
        listen       443 ssl;
        server_name  oauth.accounts.webplatform.org;

        location / {
          proxy_pass http://127.0.0.1:9010;
        }

        ssl on;
        ssl_certificate     ssl/oauth.accounts.webplatform-20140401.pem;
        ssl_certificate_key ssl/201404.key;
        ssl_session_timeout 5m;
        ssl_protocols SSLv3 TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers "HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES";
        ssl_prefer_server_ciphers on;
    }

Remove default nginx vhost

    rm /etc/nginx/sites-enabled/default

Return as normal user

    exit

## <span>Create self-signed certificates</span>

Paste our own self-signed CA authority (eventually will be real ones)

    vi ca-cert.pem
    vi ca-key.pem

*Optionnal* If you do not have your own certs to use as root of your own self-signed authority, you can make your own with this:

    openssl genrsa 2048 > ca-key.pem

    openssl req -new -x509 -nodes -days 3600 \
        -key ca-key.pem -out ca-cert.pem

Generate certificate request:

    openssl req -newkey rsa:2048 -days 3600 -nodes -keyout server-key.pem -out accounts-req.pem -subj '/C=US/ST=MA/L=Cambridge/O=W3C/OU=WebPlatform Project/CN=accounts.webplatform.org/emailAddress=hostmaster@webplatform.org'

    openssl req -newkey rsa:2048 -days 3600 -nodes -keyout server-key.pem -out api.accounts-req.pem -subj '/C=US/ST=MA/L=Cambridge/O=W3C/OU=WebPlatform Project/CN=api.accounts.webplatform.org/emailAddress=hostmaster@webplatform.org'

Generate self-signed certificate:

    openssl x509 -req -in accounts-req.pem -days 3600 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out accounts-cert.pem

    openssl x509 -req -in api.accounts-req.pem -days 3600 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out api.accounts-cert.pem

As described in [NGINX SSL Module documentation about SSL certificates](http://wiki.nginx.org/HttpSslModule#Generate_Certificates);

> When using a chain of certificates, just append the extra certificates to your .crt file. The server certificate needs to be the first on the file, otherwise you'll get a mismatch between private and public keys.

Rename them fo follow the conventions given in the rest of the procedure.

    mv accounts-cert.pem accounts.webplatform-20140401.pem
    cat ca-cert.pem >> accounts.webplatform-20140401.pem

    mv api.accounts-cert.pem api.accounts.webplatform-20140401.pem
    cat ca-cert.pem >> api.accounts.webplatform-20140401.pem

    mv server-key.pem 201404.key