---
title: WPD:Infrastructure/procedures/Installing and theme Firefox accounts
---
<p>Canonical version <a rel="nofollow" class="external text" href="https://gist.github.com/renoirb/81a3544bce3a5831e793">published in this gist</a>
</p>
<h1><span class="mw-headline" id="Installing_Firefox_Accounts_.28.22FxA.22.29">Installing Firefox Accounts (&quot;FxA&quot;)</span></h1>
<p>Procedure to install <a rel="nofollow" class="external text" href="https://wiki.mozilla.org/Identity/Firefox_Accounts">Firefox Accounts system</a> to <a rel="nofollow" class="external text" href="http://www.webplatform.org/">WebPlatform</a> infrastructure.
</p><p>It requires a set of components:
</p>
<ul><li> <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-content-server">Firefox Accounts Content server</a> that holds the HTML/CSS/JavaScript files for the frontend<br /></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-auth-server">Firefox Accounts Authentication server</a><br /></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-profile-server">Firefox Accounts Profile server</a><br /></li>
<li> <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-oauth-server">Firefox Accounts OAuth server</a></li></ul>
<h1><span class="mw-headline" id="Misc_notes">Misc notes</span></h1>
<ul><li> <a rel="nofollow" class="external free" href="https://github.com/mozilla/fxa-oauth-server">https://github.com/mozilla/fxa-oauth-server</a><br /></li>
<li> <a rel="nofollow" class="external free" href="https://github.com/mozilla/fxa-oauth-server/wiki/oauth-design">https://github.com/mozilla/fxa-oauth-server/wiki/oauth-design</a></li></ul>
<h2><span class="mw-headline" id="OAuth_terminology_regarding_grants.2Froles.2Fentitlement">OAuth terminology regarding grants/roles/entitlement</span></h2>
<blockquote>seanmonstar: ... the oauth spec uses &quot;grant&quot; where we use &quot;code&quot;. OAuth server sends a code to app, and the app trades the &quot;code&quot; for a token.
</blockquote>
<h1><span class="mw-headline" id="Procedure">Procedure</span></h1>
<h2><span class="mw-headline" id="Install_Firefox_Content_server">Install Firefox Content server</span></h2>
<p>Basic system utilities
</p>
<pre>sudo apt-get install nginx-full git nodejs npm</pre>
<p>Ubuntu package-names collision fix, we want nodejs, not radio amateur utility.
</p>
<pre>sudo ln -s /usr/bin/nodejs /usr/bin/node</pre>
<p>Deployment specific requirements:
</p>
<pre>sudo apt-get install libgmp-dev libgmp10
sudo npm install -g grunt-cli phantomjs bower bunyan forever</pre>
<p>Creating folder:
</p>
<pre>sudo mkdir -p /srv/webplatform/auth/fxa-content-server
sudo chown -R ubuntu:ubuntu /srv/webplatform</pre>
<p>Project dependencies
</p>
<pre>cd /srv/webplatform/auth/fxa-content-server
git clone https://github.com/mozilla/fxa-content-server.git .</pre>
<p>Checkout the latest <code>train-X</code> they have available. Both auth and content projects should have matching branches.
</p>
<pre>git branch -r
git checkout -t origin/train-11</pre>
<p>Install dependencies
</p>
<pre>npm install
bower install</pre>
<p>Available configuration options, through Convict
</p>
<pre>cp server/config/local.json-dist server/config/local.json</pre>
<p>Note that the <code>local.json</code> is in the gitignore and is used by default so you do not need to set command line argument to specify which configuration file to load.
</p><p><b>Configuration</b>, refer to <a rel="nofollow" class="external text" href="https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-content-server">fxa-content-server</a> config block below.
</p><p>Note that you can see available options the project base Convict file.
</p>
<pre>more server/lib/configuration.js</pre>
<p>Configuration notes:
</p>
<ul><li> <code>fxaccount_url</code>: Is where you will expose the <i>fxa-auth-server</i>, ideally through a HTTP server that has a valid SSL certificate, in our case <code>api.accounts.webplatform.org</code></li></ul>
<p>Start the service:
</p>
<pre>grunt server:dist</pre>
<p>This command will take care to compile all assets into static ones, and make a local HTTP server so we can use NGINX to forward to it.
</p><p><i>Process runner:</i> Ideally this should be ran through a process runner (forever) and logs should be sent to a logger. #TODO
</p><p><i>NOTE</i> It has been validated with <code>zaach</code> that content-server requires nodejs. Therefore we cannot just use an HTTP server to serve file, they are not fully static.
</p>
<h2><span class="mw-headline" id="Install_Firefox_Account_Authentication_service">Install Firefox Account Authentication service</span></h2>
<p>Clone the project
</p>
<pre>cd /srv/webplatform/auth
git clone git://github.com/mozilla/fxa-auth-server.git
cd fxa-auth-server</pre>
<p>Checkout the latest <code>train-X</code> they have available.
</p>
<pre>git branch -r
git checkout -t origin/train-10</pre>
<p>Install dependencies
</p>
<pre>npm install</pre>
<p><b>Configuration</b>, refer to <a rel="nofollow" class="external text" href="https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-auth-server">fxa-auth-server</a> config block below.
</p><p>Note that you can see available options the project base Convict file.
</p>
<pre>more config/config.js</pre>
<p>The file name can match the environment name. For example, if you use <code>NODE_ENV=prod</code>, the file would be <code>config/prod.json</code>
</p><p>Notes about the keys:
</p>
<ul><li> <code>contentServer</code>: Is the URL where the <i>fxa-content-server</i> is<br /></li>
<li> <code>templateServer</code>: Is, also, where the <i>fxa-content-server</i> is (in case you want a different address)</li></ul>
<h2><span class="mw-headline" id="Install_OAuth_service">Install OAuth service</span></h2>
<p>Clone the project
</p>
<pre>cd /srv/webplatform/auth
git clone git://github.com/mozilla/fxa-oauth-server.git
cd fxa-oauth-server
git checkout -t origin/master</pre>
<p>Install dependencies
</p>
<pre>npm install</pre>
<p><b>Configuration</b>, refer to <a rel="nofollow" class="external text" href="https://gist.github.com/renoirb/81a3544bce3a5831e793#fxa-oauth-server">fxa-oauth-server</a> config block below.
</p><p>You can see the available configuration switches here:
</p>
<pre>more lib/config.js
more config/dev.json</pre>
<p>Note that the <code>clients</code> array will ensure that the services are inserted in the database. This is how you allow a service to authenticate against the service.
</p><p>Note also the <code>whitelisted</code>, this property is useful to differentiate services that we want to pass through OAuth without asking each user to confirm the use. To learn more about generating keys, you can see it in the <a rel="nofollow" class="external text" href="https://github.com/mozilla/fxa-oauth-server/blob/master/docs/clients.md">fxa-oauth-server/doc/clients.md</a>
</p>
<h2><span class="mw-headline" id="Configure_NGINX">Configure NGINX</span></h2>
<p>Note, we are creating self-signed for the moment.
</p>
<pre>sudo -s
cd /etc/nginx/ssl</pre>
<p>From here, you have two choices:
</p>
<ul><li> Install your key and certificates<br /></li>
<li> Create self-signed certificates</li></ul>
<p>It is expected that you have the following files in <code>/etc/nginx/ssl</code>
</p><p>Adjust vhost:
</p>
<pre>vi /etc/nginx/sites-enabled/accounts</pre>
<p>Paste:
</p>
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
<p>Remove default nginx vhost
</p>
<pre>rm /etc/nginx/sites-enabled/default</pre>
<p>Return as normal user
</p>
<pre>exit</pre>
<h2><span class="mw-headline" id="Create_self-signed_certificates">Create self-signed certificates</span></h2>
<p>Paste our own self-signed CA authority (eventually will be real ones)
</p>
<pre>vi ca-cert.pem
vi ca-key.pem</pre>
<p><i>Optionnal</i> If you do not have your own certs to use as root of your own self-signed authority, you can make your own with this:
</p>
<pre>openssl genrsa 2048 &gt; ca-key.pem

openssl req -new -x509 -nodes -days 3600 \
    -key ca-key.pem -out ca-cert.pem</pre>
<p>Generate certificate request:
</p>
<pre>openssl req -newkey rsa:2048 -days 3600 -nodes -keyout server-key.pem -out accounts-req.pem -subj '/C=US/ST=MA/L=Cambridge/O=W3C/OU=WebPlatform Project/CN=accounts.webplatform.org/emailAddress=hostmaster@webplatform.org'

openssl req -newkey rsa:2048 -days 3600 -nodes -keyout server-key.pem -out api.accounts-req.pem -subj '/C=US/ST=MA/L=Cambridge/O=W3C/OU=WebPlatform Project/CN=api.accounts.webplatform.org/emailAddress=hostmaster@webplatform.org'</pre>
<p>Generate self-signed certificate:
</p>
<pre>openssl x509 -req -in accounts-req.pem -days 3600 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out accounts-cert.pem

openssl x509 -req -in api.accounts-req.pem -days 3600 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out api.accounts-cert.pem</pre>
<p>As described in <a rel="nofollow" class="external text" href="http://wiki.nginx.org/HttpSslModule#Generate_Certificates">NGINX SSL Module documentation about SSL certificates</a>;
</p>
<blockquote>When using a chain of certificates, just append the extra certificates to your .crt file. The server certificate needs to be the first on the file, otherwise you'll get a mismatch between private and public keys.
</blockquote>
<p>Rename them fo follow the conventions given in the rest of the procedure.
</p>
<pre>mv accounts-cert.pem accounts.webplatform-20140401.pem
cat ca-cert.pem &gt;&gt; accounts.webplatform-20140401.pem

mv api.accounts-cert.pem api.accounts.webplatform-20140401.pem
cat ca-cert.pem &gt;&gt; api.accounts.webplatform-20140401.pem

mv server-key.pem 201404.key</pre>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:19844-0!*!*!!*!*!*!esi=1 and timestamp 20150731185138 and revision id 54756
 -->
