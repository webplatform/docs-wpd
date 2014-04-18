== Installing and skin for WebPlatform Docs the Firefox Accounts ==

=== Procedure (raw) ===
* Start with latest trusty Ubuntu machine
<syntaxHighlight>
sudo apt-get install nginx-full git nodejs npm
sudo apt-get install libgmp-dev libgmp10

sudo mkdir -p /srv/webplatform/auth/fxa-content-server
sudo chown -R ubuntu:ubuntu /srv/webplatform

cd /srv/webplatform/auth/fxa-content-server
git clone https://github.com/mozilla/fxa-content-server.git .
sudo npm install -g grunt-cli phantomjs bower
npm install
bower install
more server/lib/configuration.js
cp server/config/production.json server/config/webplatform_prod.json
CONFIG_FILES=./config/webplatform_prod.json grunt server:dist
sudo npm install -g bunyan
</syntaxHighlight>