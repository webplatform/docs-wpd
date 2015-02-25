= How MediaWiki backend sees an HTTP request. With or without Fastly in front =

This page shows two equivalent browsing sessions. One was made with Fastly, and the other without.

== Go to Edit Form ==
=== Without Fastly ===
<syntaxHighlight lang="text">
Start request GET /w/index.php?title=Special:UserLogin&returnto=WPD%3AInfrastructure%2Farchitecture%2FVM+roles
HTTP HEADERS:
HOST: docs.webplatform.org
CONNECTION: keep-alive
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=Special:UserLogout&returnto=WPD%3AInfrastructure%2Farchitecture%2FVM+roles
ACCEPT-ENCODING: gzip, deflate, sdch
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: _pk_ref.1.6aa5=%5B%22%22%2C%22%22%2C1424138557%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FPublic%2Fpublic-webplatform%2F2015Feb%2F0003.html%22%5D; _pk_id.1.6aa5=f60e7f3954913aa0.1420732750.108.1424138557.1424116005.; _pk_ref.9.6aa5=%5B%22%22%2C%22%22%2C1424182609%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FTeam%2Fw3t-sys%2F2015JanFeb%2F0093.html%22%5D; _pk_id.9.6aa5=ea6c3462853cd2d6.1421114716.7.1424182620.1422055058.; wptestwiki_session=37ad13fe80ea727fdbb89a1870dbb29c; wptestwikiUserID=150; wptestwikiUserName=Renoirb; _pk_ref.1.db2a=%5B%22%22%2C%22%22%2C1424897026%2C%22http%3A%2F%2Fwww.baidu.com%2Fs%3Fwd%3Dhtml%7Btouch-action%3Anone%3B%7D%22%5D; wpwikiUserName=Renoirb; wpwiki_session=mf5fir53lg7c2ao641o9pfjmn3; wpwikiLoggedOut=1424900841; _pk_id.1.db2a=e07e1a4d4c024be6.1424134581.36.1424900843.1424887118.; _pk_ses.1.db2a=*
FASTLY-DEBUG: true
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
MessageCache::load: Loading en... got from global cache
IP: 173.178.131.114
MWCryptRand::realGenerate: Generating cryptographic random bytes for LoginForm::setLoginToken/MWCryptRand::generateHex/MWCryptRand::realGenerateHex/MWCryptRand::generate/MWCryptRand::realGenerate
MWCryptRand::realGenerate: openssl_random_pseudo_bytes generated 16 bytes of strong randomness.
MWCryptRand::realGenerate: 0 bytes of randomness leftover in the buffer.
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Unstubbing $wgLang on call of $wgLang::_unstub from ParserOptions::__construct
OutputPage::sendCacheControl: private caching;  **
Request ended normally
</syntaxHighlight>

=== With Fastly ===
<SyntaxHighlight  lang="text">
Start request GET /w/index.php?title=WPD:Infrastructure/architecture/VM_roles&action=edit
HTTP HEADERS:
HOST: docs.webplatform.org
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/wiki/WPD:Infrastructure/architecture/VM_roles
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
FASTLY-DEBUG: true
FASTLY-CLIENT-IP: 173.178.131.114
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.114, 173.178.131.114
COOKIE: wpwikiLoggedOut=1424902515; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06
X-VARNISH: 4100626631, 438482695
ACCEPT-ENCODING: gzip
FASTLY-CLIENT: 1
X-FORWARDED-FOR: 173.178.131.114, 173.178.131.114
FASTLY-FF: cache-atl6221-ATL, cache-atl6223-ATL
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
User: got user 10080 from cache
User: loading options for user 10080 from override cache.
User: logged in from session
EditPage::edit: enter
EditPage::importFormData: Not a posted form.
SFUtils::showFormPreview: enter.
User: loading options for user 10080 from override cache.
User::getBlockedStatus: checking...
MessageCache::load: Loading en... got from global cache
Unstubbing $wgLang on call of $wgLang::getCode from MessageCache::getMessageFromFallbackChain
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
OutputPage::sendCacheControl: private caching;  **
Request ended normally
</SyntaxHighlight>