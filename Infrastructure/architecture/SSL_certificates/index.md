---
title: WPD:Infrastructure/architecture/SSL certificates
---
<h1><span class="mw-headline" id="SSL_Certificates">SSL Certificates</span></h1>
<p>To manage our SSL certificates we copy around an encrypted file that holds our keys and certificates for our environments. Its maybe not the best method but we’ll keep it that way until we work on improving it.
</p>
<h2><span class="mw-headline" id="Design_decisions">Design decisions</span></h2>
<dl><dt> We do not want to have to enter a passphrase at every web server restart or server reboot</dt>
<dd> we are then stuck to copy around private keys and certificates that aren’t passphrase protected</dd>
<dt> We want to rebuild any VM at any time</dt>
<dd> We therefore need to make available the certificates so they can be rsync’ed at any time</dd>
<dt> We want to have a quick VM creation process</dt>
<dd> That’s why we have salt, but we cannot encrypt/decrypt certificate archive at every time</dd></dl>
<p>It means that we’ll ensure that as few people as possible has access to the salt master as its where the certificates file is hosted decrypted.
</p>
<h2><span class="mw-headline" id="Where_are_the_files">Where are the files</span></h2>
<ul><li> The file is called <b>certificates.tar.gz.gpg</b> and its hosted in DreamObjects <b>wpd-ci</b> bucket.</li>
<li> The file gets download on the salt master at <b>/srv/code/packages/</b> where <b>certificates.tar.gz.gpg</b> is kept decrypted, and decompressed.</li>
<li> The file <b>/srv/code/packages/certificates.README.md</b> has a copy of this document in the wiki at <a rel="nofollow" class="external free" href="https://docs.webplatform.org/wiki/WPD:Infrastructure/architecture/SSL_certificates">https://docs.webplatform.org/wiki/WPD:Infrastructure/architecture/SSL_certificates</a></li></ul>
<h2><span class="mw-headline" id="Certificates_package_convention">Certificates package convention</span></h2>
<p>New convention is based on this <b>certificates/foo/public_bar_bazz.pem</b> 
</p>
<ul><li> <i>public</i> represents whether or not its a certificate from a CA. It’ll be useful when we’ll use self-signed that we wouldn’t expose to the public.</li>
<li> <i>foo</i> represents the environment level (e.g. production)</li>
<li> Each file MUST have its equivalent any 'foo' folder (i.e. each environment we manage)</li>
<li> <i>bar</i> represents an identifier, one word should be fine (e.g. wildcard)</li>
<li> <i>bazz</i> represents the private key that was used to generate the CSR</li>
<li> The file MUST be decrypted and extracted on the salt master at <b>/srv/code/packages/certificates</b> so that deployment state at <b>code.certificates</b> copies it where its expected</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="What.E2.80.99s_the_domain_names_for_a_certificate.3F">What’s the domain names for a certificate?</span></h2>
<p>Run
</p>
<pre> openssl x509 -text -in certificates/production/public_accounts_subdomains_201404.pem | grep 'DNS:'
</pre>
<p>Will list them like this:
</p>
<pre> DNS:accounts.webplatform.org, DNS:webplatform.org, DNS:profile.accounts.webplatform.org, DNS:verifier.accounts.webplatform.org, DNS:certifier.accounts.web
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Testing_certificate_from_the_terminal">Testing certificate from the terminal</span></h2>
<pre> openssl s_client -connect 173.236.254.96:443 -servername accounts.webplatform.org -CApath /etc/ssl/certs/  &lt; /dev/null | openssl x509 -text | grep 'DNS:'
</pre>
<p>Where:
</p>
<dl><dt> 173.236.254.96</dt>
<dd> is the IP address of the server you just deployed certificates</dd>
<dt> accounts.webplatform.org</dt>
<dd> is the domain name you want to test</dd></dl>
<p>Should look like this:
</p>
<pre> DNS:notes.webplatform.org, DNS:docs.webplatform.org, DNS:accounts.webplatform.org, DNS:specs.webplatform.org, DNS:www.webplatform.org, DNS:webplatform.org
</pre>
<p><br />
</p>
<h2><span class="mw-headline" id="Updating_the_certificate_archive">Updating the certificate archive</span></h2>
<pre>   tar cfz certificates.tar.gz certificates
   gpg -c certificates.tar.gz
   source /srv/ci-dreamobjects.sh
   swift upload wpd-packages certificates.tar.gz.gpg
</pre>
<p>Passphrase should be known by <b>renoirb</b> and <b>shepazu</b>.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Extracting_data">Extracting data</span></h2>
<p><b>Note</b>: this is done automatically at <i>/srv/salt/_utils/new-saltmaster-packages.sh</i> when we create a new salt master.
</p>
<pre>   gpg certificates.tar.gz.gpg
   tar xfz certificates.tar.gz
</pre>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:58627-0!*!*!!*!*!*!esi=1 and timestamp 20150731185851 and revision id 101129
 -->
