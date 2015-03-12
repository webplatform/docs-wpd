= SSL Certificates =

To manage our SSL certificates we copy around an encrypted file that holds our keys and certificates for our environments. Its maybe not the best method but we’ll keep it that way until we work on improving it.

== Design decisions ==

; We do not want to have to enter a passphrase at every web server restart or server reboot: we are then stuck to copy around private keys and certificates that aren’t passphrase protected
; We want to rebuild any VM at any time: We therefore need to make available the certificates so they can be rsync’ed at any time
; We want to have a quick VM creation process: That’s why we have salt, but we cannot encrypt/decrypt certificate archive at every time

It means that we’ll ensure that as few people as possible has access to the salt master as its where the certificates file is hosted decrypted.

== Where are the files ==

* The file is called '''certificates.tar.gz.gpg''' and its hosted in DreamObjects '''wpd-ci''' bucket.
* The file gets download on the salt master at ''/srv/code/packages/''' where '''certificates.tar.gz.gpg''' is kept decrypted, and decompressed.
* The file '''/srv/code/packages/certificates.README.md''' has a copy of this document in the wiki 

==  Certificates package convention ==

New convention is based on this `certificates/foo/public_bar_bazz.pem` 

* 'public' represents whether or not its a certificate from a CA. It’ll be useful when we’ll use self-signed that we wouldn’t expose to the public.
* 'foo' represents the environment level (e.g. production)
* Each file MUST have its equivalent any 'foo' folder (i.e. each environment we manage)
* 'bar' represents an identifier, one word should be fine (e.g. wildcard)
* 'bazz' represents the private key that was used to generate the CSR
* MUST be on the salt master at '''/srv/code/packages'''


== What’s the domain names for a certificate? ==

Run

    openssl x509 -text -in certificates/production/public_accounts_subdomains_201404.pem | grep 'DNS:'

Will list them like this:

    DNS:accounts.webplatform.org, DNS:webplatform.org, DNS:profile.accounts.webplatform.org, DNS:verifier.accounts.webplatform.org, DNS:certifier.accounts.web



## Testing certificate from the terminal

    openssl s_client -connect 173.236.254.96:443 -servername api.accounts.webplatform.org -CApath /etc/ssl/certs/  < /dev/null | openssl x509 -text

Where

* '173.236.254.96' is the IP address of the server you just deployed certificates
* 'api.accounts.webplatform.org is the domain name you want to test



== Updating the certificate archive ==

    tar cfz certificates.tar.gz certificates
    gpg -c certificates.tar.gz
    source /srv/ci-dreamobjects.sh
    swift upload wpd-packages certificates.tar.gz.gpg

Passphrase should be known by '''renoirb''' and '''shepazu'''.


== Extracting data ==

*note*: This is done automatically at `/srv/salt/_utils/new-saltmaster-packages.sh`

    gpg certificates.tar.gz.gpg
    tar xfz certificates.tar.gz