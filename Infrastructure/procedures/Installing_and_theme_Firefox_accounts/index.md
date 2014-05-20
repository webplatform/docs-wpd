Canonical version [https://gist.github.com/renoirb/81a3544bce3a5831e793 published in this gist]

= Installing Firefox Accounts (&quot;FxA&quot;) =
Procedure to install [https://wiki.mozilla.org/Identity/Firefox_Accounts Firefox Accounts system] to [http://www.webplatform.org/ WebPlatform] infrastructure.

It requires a set of components:

* [https://github.com/mozilla/fxa-content-server Firefox Accounts Content server] that holds the HTML/CSS/JavaScript files for the frontend<br />
* [https://github.com/mozilla/fxa-auth-server Firefox Accounts Authentication server]<br />
* [https://github.com/mozilla/fxa-profile-server Firefox Accounts Profile server]<br />
* [https://github.com/mozilla/fxa-oauth-server Firefox Accounts OAuth server]

= Misc notes =

* https://github.com/mozilla/fxa-oauth-server<br />
* https://github.com/mozilla/fxa-oauth-server/wiki/oauth-design

== OAuth terminology regarding grants/roles/entitlement ==

<blockquote>seanmonstar: ... the oauth spec uses &quot;grant&quot; where we use &quot;code&quot;. OAuth server sends a code to app, and the app trades the &quot;code&quot; for a token.
</blockquote>
= Procedure =

== Install Firefox Content server ==

Basic system utilities

<pre>sudo apt-get install nginx-full git nodejs npm</pre>
Ubuntu package-names collision fix, we want nodejs, not radio amateur utility.

<pre>sudo ln -s /usr/bin/nodejs /usr/bin/node</pre>
Deployment specific requirements:

<pre>sudo apt-get install libgmp-dev libgmp10
sudo npm install -g grunt-cli phantomjs bower bunyan forever</pre>
Creating folder:

<pre>sudo mkdir -p /srv/webplatform/auth/fxa-content-server
sudo chown -R ubuntu:ubuntu /srv/webplatform</pre>
Project dependencies

<pre>cd /srv/webplatform/auth/fxa-content-server
git clone https://github.com/mozilla/fxa-content-server.git .</pre>
Checkout the latest <code>train-X</code> they have available. Both auth and content projects should have matching branches.

<pre>git branch -r
git checkout -t origin/train-11</pre>
Install dependencies

<pre>npm install
bower install</pre>
Available configuration options, through Convict

<pre>cp server/config/local.json-dist server/config/local.json</pre>
Note that the <code>local.json</code> is in the gitignore and is used by default so you do not need to set command line argument to specify which configuration file to load.

'''Configuration''', refer to [https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-content-server fxa-content-server] config block below.

Note that you can see available options the project base Convict file.

<pre>more server/lib/configuration.js</pre>
Configuration notes:

* <code>fxaccount_url</code>: Is where you will expose the ''fxa-auth-server'', ideally through a HTTP server that has a valid SSL certificate, in our case <code>api.accounts.webplatform.org</code>

Start the service:

<pre>grunt server:dist</pre>
This command will take care to compile all assets into static ones, and make a local HTTP server so we can use NGINX to forward to it.

''Process runner:'' Ideally this should be ran through a process runner (forever) and logs should be sent to a logger. #TODO

''NOTE'' It has been validated with <code>zaach</code> that content-server requires nodejs. Therefore we cannot just use an HTTP server to serve file, they are not fully static.

== Install Firefox Account Authentication service ==

Clone the project

<pre>cd /srv/webplatform/auth
git clone git://github.com/mozilla/fxa-auth-server.git
cd fxa-auth-server</pre>
Checkout the latest <code>train-X</code> they have available.

<pre>git branch -r
git checkout -t origin/train-10</pre>
Install dependencies

<pre>npm install</pre>
'''Configuration''', refer to [https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-auth-server fxa-auth-server] config block below.

Note that you can see available options the project base Convict file.

<pre>more config/config.js</pre>
The file name can match the environment name. For example, if you use <code>NODE_ENV=prod</code>, the file would be <code>config/prod.json</code>

Notes about the keys:

* <code>contentServer</code>: Is the URL where the ''fxa-content-server'' is<br />
* <code>templateServer</code>: Is, also, where the ''fxa-content-server'' is (in case you want a different address)

== Install OAuth service ==

Clone the project

<pre>cd /srv/webplatform/auth
git clone git://github.com/mozilla/fxa-oauth-server.git
cd fxa-oauth-server
git checkout -t origin/master</pre>
Install dependencies

<pre>npm install</pre>
'''Configuration''', refer to [https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-oauth-server fxa-oauth-server] config block below.

You can see the available configuration switches here:

<pre>more lib/config.js
more config/dev.json</pre>
Note that the <code>clients</code> array will ensure that the services are inserted in the database. This is how you allow a service to authenticate against the service.

Note also the <code>whitelisted</code>, this property is useful to differentiate services that we want to pass through OAuth without asking each user to confirm the use. To learn more about generating keys, you can see it in the [https://github.com/mozilla/fxa-oauth-server/blob/master/docs/clients.md fxa-oauth-server/doc/clients.md]

== Configure NGINX ==

Note, we are creating self-signed for the moment.

<pre>sudo -s
cd /etc/nginx/ssl</pre>
From here, you have two choices:

* Install your key and certificates<br />
* Create self-signed certificates

It is expected that you have the following files in <code>/etc/nginx/ssl</code>

Adjust vhost:

<pre>vi /etc/nginx/sites-enabled/accounts</pre>
Paste:

<pre>server {
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
    ssl_ciphers &quot;HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES&quot;;
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
    ssl_ciphers &quot;HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES&quot;;
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
    ssl_ciphers &quot;HIGH:!aNULL:!MD5 or HIGH:!aNULL:!MD5:!3DES&quot;;
    ssl_prefer_server_ciphers on;
}</pre>
Remove default nginx vhost

<pre>rm /etc/nginx/sites-enabled/default</pre>
Return as normal user

<pre>exit</pre>
== Create self-signed certificates ==

Paste our own self-signed CA authority (eventually will be real ones)

<pre>vi ca-cert.pem
vi ca-key.pem</pre>
''Optionnal'' If you do not have your own certs to use as root of your own self-signed authority, you can make your own with this:

<pre>openssl genrsa 2048 &gt; ca-key.pem

openssl req -new -x509 -nodes -days 3600 \
    -key ca-key.pem -out ca-cert.pem</pre>
Generate certificate request:

<pre>openssl req -newkey rsa:2048 -days 3600 -nodes -keyout server-key.pem -out accounts-req.pem -subj '/C=US/ST=MA/L=Cambridge/O=W3C/OU=WebPlatform Project/CN=accounts.webplatform.org/emailAddress=hostmaster@webplatform.org'

openssl req -newkey rsa:2048 -days 3600 -nodes -keyout server-key.pem -out api.accounts-req.pem -subj '/C=US/ST=MA/L=Cambridge/O=W3C/OU=WebPlatform Project/CN=api.accounts.webplatform.org/emailAddress=hostmaster@webplatform.org'</pre>
Generate self-signed certificate:

<pre>openssl x509 -req -in accounts-req.pem -days 3600 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out accounts-cert.pem

openssl x509 -req -in api.accounts-req.pem -days 3600 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out api.accounts-cert.pem</pre>
As described in [http://wiki.nginx.org/HttpSslModule#Generate_Certificates NGINX SSL Module documentation about SSL certificates];

<blockquote>When using a chain of certificates, just append the extra certificates to your .crt file. The server certificate needs to be the first on the file, otherwise you'll get a mismatch between private and public keys.
</blockquote>
Rename them fo follow the conventions given in the rest of the procedure.

<pre>mv accounts-cert.pem accounts.webplatform-20140401.pem
cat ca-cert.pem &gt;&gt; accounts.webplatform-20140401.pem

mv api.accounts-cert.pem api.accounts.webplatform-20140401.pem
cat ca-cert.pem &gt;&gt; api.accounts.webplatform-20140401.pem

mv server-key.pem 201404.key</pre>