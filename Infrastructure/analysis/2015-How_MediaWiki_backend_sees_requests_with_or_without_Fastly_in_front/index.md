= How MediaWiki backend sees an HTTP request. With or without Fastly in front =

This page shows two equivalent browsing sessions. One was made with Fastly, and the other without.

== Description ==

The purpose of this is to illustrate the difference in how MediaWiki backend processes what it gets from the browsers depending of whether or not Fastly is present.

Things to notice:
# Cookies are trimmed; only the ones starting with ''wpwiki'' are passed to the backend
# ''Forwarded-For'' headers and their temporary counterparts

== Actions ==
=== Go to Edit Form ===
==== Without Fastly ====
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
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
MessageCache::load: Loading en... got from global cache
IP: 173.178.131.111
MWCryptRand::realGenerate: Generating cryptographic random bytes for LoginForm::setLoginToken/MWCryptRand::generateHex/MWCryptRand::realGenerateHex/MWCryptRand::generate/MWCryptRand::realGenerate
MWCryptRand::realGenerate: openssl_random_pseudo_bytes generated 16 bytes of strong randomness.
MWCryptRand::realGenerate: 0 bytes of randomness leftover in the buffer.
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Unstubbing $wgLang on call of $wgLang::_unstub from ParserOptions::__construct
OutputPage::sendCacheControl: private caching;  **
Request ended normally
</syntaxHighlight>

==== With Fastly ====
<SyntaxHighlight  lang="text">
Start request GET /w/index.php?title=WPD:Infrastructure/architecture/VM_roles&action=edit
HTTP HEADERS:
HOST: docs.webplatform.org
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/wiki/WPD:Infrastructure/architecture/VM_roles
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
FASTLY-CLIENT-IP: 173.178.131.111
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.111, 173.178.131.111
COOKIE: wpwikiLoggedOut=1424902515; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06
X-VARNISH: 4100626631, 438482695
ACCEPT-ENCODING: gzip
FASTLY-CLIENT: 1
X-FORWARDED-FOR: 173.178.131.111, 173.178.131.111
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


=== Submit Form, view page ===
==== Without Fastly ====
<syntaxHighlight lang="text">
Start request POST /w/index.php?title=Special:UserLogin&action=submitlogin&type=login&returnto=WPD:Infrastructure/architecture/VM+roles
HTTP HEADERS:
HOST: docs.webplatform.org
CONNECTION: keep-alive
CONTENT-LENGTH: 108
CACHE-CONTROL: max-age=0
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
ORIGIN: https://docs.webplatform.org
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
CONTENT-TYPE: application/x-www-form-urlencoded
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=Special:UserLogin&returnto=WPD%3AInfrastructure%2Farchitecture%2FVM+roles
ACCEPT-ENCODING: gzip, deflate
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: _pk_ref.1.6aa5=%5B%22%22%2C%22%22%2C1424138557%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FPublic%2Fpublic-webplatform%2F2015Feb%2F0003.html%22%5D; _pk_id.1.6aa5=f60e7f3954913aa0.1420732750.108.1424138557.1424116005.; _pk_ref.9.6aa5=%5B%22%22%2C%22%22%2C1424182609%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FTeam%2Fw3t-sys%2F2015JanFeb%2F0093.html%22%5D; _pk_id.9.6aa5=ea6c3462853cd2d6.1421114716.7.1424182620.1422055058.; wptestwiki_session=37ad13fe80ea727fdbb89a1870dbb29c; wptestwikiUserID=150; wptestwikiUserName=Renoirb; _pk_ref.1.db2a=%5B%22%22%2C%22%22%2C1424897026%2C%22http%3A%2F%2Fwww.baidu.com%2Fs%3Fwd%3Dhtml%7Btouch-action%3Anone%3B%7D%22%5D; wpwikiUserName=Renoirb; wpwiki_session=mf5fir53lg7c2ao641o9pfjmn3; wpwikiLoggedOut=1424900841; _pk_id.1.db2a=e07e1a4d4c024be6.1424134581.36.1424900895.1424887118.; _pk_ses.1.db2a=*
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
MessageCache::load: Loading en... got from global cache
IP: 173.178.131.111
User: got user 10080 from cache
[cookie] setcookie: "wpwikiUserID", "10080", "1440452895", "/", "", "1", "1"
[cookie] setcookie: "wpwikiUserName", "Renoirb", "1440452895", "/", "", "1", "1"
[cookie] setcookie: "wpwikiToken", "", "1424814495", "/", "", "1", "1"
User: loading options for user 10080 from override cache.
DatabaseBase::query: Writes done: UPDATE `user` SET user_touched = 'X')
OutputPage::sendCacheControl: private caching;  **
Request ended normally


Start request GET /wiki/WPD:Infrastructure/architecture/VM_roles
HTTP HEADERS:
HOST: docs.webplatform.org
CONNECTION: keep-alive
CACHE-CONTROL: max-age=0
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=Special:UserLogin&returnto=WPD%3AInfrastructure%2Farchitecture%2FVM+roles
ACCEPT-ENCODING: gzip, deflate, sdch
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: _pk_ref.1.6aa5=%5B%22%22%2C%22%22%2C1424138557%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FPublic%2Fpublic-webplatform%2F2015Feb%2F0003.html%22%5D; _pk_id.1.6aa5=f60e7f3954913aa0.1420732750.108.1424138557.1424116005.; _pk_ref.9.6aa5=%5B%22%22%2C%22%22%2C1424182609%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FTeam%2Fw3t-sys%2F2015JanFeb%2F0093.html%22%5D; _pk_id.9.6aa5=ea6c3462853cd2d6.1421114716.7.1424182620.1422055058.; wptestwiki_session=37ad13fe80ea727fdbb89a1870dbb29c; wptestwikiUserID=150; wptestwikiUserName=Renoirb; _pk_ref.1.db2a=%5B%22%22%2C%22%22%2C1424897026%2C%22http%3A%2F%2Fwww.baidu.com%2Fs%3Fwd%3Dhtml%7Btouch-action%3Anone%3B%7D%22%5D; wpwikiLoggedOut=1424900841; _pk_id.1.db2a=e07e1a4d4c024be6.1424134581.36.1424900895.1424887118.; _pk_ses.1.db2a=*; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=dcdcmaq5g1d067e87sr2beslr7
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
User: cache miss for user 10080
User: loading options for user 10080 from database.
User: logged in from session
User: loading options for user 10080 from override cache.
MessageCache::load: Loading en... got from global cache
OutputPage::checkLastModified: client did not send If-Modified-Since header
Article::view using parser cache: yes
Parser cache options found.
ParserOutput cache found.
Article::view: showing parser cache contents
Unstubbing $wgLang on call of $wgLang::getCode from ParserOutput::replaceEditSectionLinksCallback
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
OutputPage::sendCacheControl: private caching; Wed, 25 Feb 2015 21:48:20 GMT **
Request ended normally
</syntaxHighlight>

=== With Fastly ===
<SyntaxHighlight  lang="text">
Start request POST /w/index.php?title=WPD:Infrastructure/architecture/VM_roles&action=submit
HTTP HEADERS:
HOST: docs.webplatform.org
CACHE-CONTROL: max-age=0
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
ORIGIN: https://docs.webplatform.org
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
CONTENT-TYPE: multipart/form-data; boundary=----WebKitFormBoundary0HGHKqUos8MAYrRX
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=WPD:Infrastructure/architecture/VM_roles&action=edit
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
FASTLY-CLIENT-IP: 173.178.131.111
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
CONTENT-LENGTH: 16198
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.111, 173.178.131.111
COOKIE: wpwikiLoggedOut=1424902515; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06
ACCEPT-ENCODING: gzip
X-VARNISH: 3880587125
X-FORWARDED-FOR: 173.178.131.111, 173.178.131.111
FASTLY-FF: cache-iad2130-IAD
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
MessageCache::load: Loading en... got from global cache
EditPage::importFormData: Passed token check.
User: loading options for user 10080 from override cache.
SFUtils::showFormPreview: enter.
User::getBlockedStatus: checking...
IP: 173.178.131.111
timestamp: 20150225225143, edittime: 20150225225143
EditPage::internalAttemptSave: getting section ''
ConfirmEdit: user group allows skipping captcha
ConfirmEdit: no need to show captcha.
Unstubbing $wgParser on call of $wgParser::parse from WikitextContent::fillParserOutput
Parser: using preprocessor: Preprocessor_DOM
[Preprocessor] Saved preprocessor XML to memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:116c0786d3818b164345ef695ebc2196:1)
Pulling file metadata from cache key wpwiki:file:83bf02230c13678a2e84aed806cc506b
MimeMagic::__construct: loading mime types from /srv/webplatform/wiki/wpwiki/mediawiki/includes/mime.types
MimeMagic::__construct: loading mime info from /srv/webplatform/wiki/wpwiki/mediawiki/includes/mime.info
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
FileBackendStore::getFileStat: File mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png does not exist.
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_2624ed3fbbea-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_0382d0282548-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_5d44a03ba879-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
Unstubbing $wgLang on call of $wgLang::getCode from Message::inLanguage
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:116c0786d3818b164345ef695ebc2196:1)
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_9c3f133d0bf0-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_6e32ebd79da0-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_ba037b9a4be5-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
DatabaseBase::query: Writes done: INSERT INTO `text` (old_id,old_text,old_flags) VALUES (NULL,'X')
DatabaseBase::query: Writes done: INSERT INTO `revision` (rev_id,rev_page,rev_text_id,rev_comment,rev_minor_edit,rev_user,rev_user_text,rev_timestamp,rev_deleted,rev_len,rev_parent_id,rev_sha1,rev_content_model,rev_content_format) VALUES (NULL,'X',NULL,NULL)
DatabaseBase::query: Writes done: UPDATE `page` SET page_latest = 'X'
DatabaseBase::query: Writes done: INSERT INTO `recentchanges` (rc_timestamp,rc_namespace,rc_title,rc_type,rc_source,rc_minor,rc_cur_id,rc_user,rc_user_text,rc_comment,rc_this_oldid,rc_last_oldid,rc_bot,rc_ip,rc_patrolled,rc_new,rc_old_len,rc_new_len,rc_deleted,rc_logid,rc_log_type,rc_log_action,rc_params,rc_id) VALUES ('X',NULL)
DatabaseBase::query: Writes done: INSERT INTO `cu_changes` (cuc_id,cuc_namespace,cuc_title,cuc_minor,cuc_user,cuc_user_text,cuc_actiontext,cuc_comment,cuc_this_oldid,cuc_last_oldid,cuc_type,cuc_timestamp,cuc_ip,cuc_ip_hex,cuc_xff,cuc_xff_hex,cuc_agent,cuc_page_id) VALUES (NULL,'X')
DatabaseBase::query: Writes done: INSERT INTO `logging` (log_id,log_type,log_action,log_timestamp,log_user,log_user_text,log_namespace,log_title,log_page,log_comment,log_params) VALUES (NULL,'X')
DatabaseBase::query: Writes done: UPDATE `user` SET user_editcount=user_editcount+N WHERE user_id = 'X'
DatabaseBase::query: Writes done: UPDATE `user` SET user_touched = 'X')
WikiPage::doEditUpdates: No vary-revision, using prepared edit...
Saved in parser cache with key wpwiki:pcache:idhash:58597-0!*!0!!*!2!*!esi=1 and timestamp 20150225225555 and revision id 100865
DatabaseBase::query: Writes done: UPDATE `page` SET page_touched = 'X'
DatabaseBase::query: Writes done: UPDATE `page` SET page_links_updated = 'X'
BacklinkCache::queryLinks: got results from DB
[cookie] setcookie: "wpwikiPostEditRevision100865", "saved", "1424906155", "/", "", "", ""
OutputPage::sendCacheControl: private caching;  **
DatabaseBase::query: Writes done: UPDATE `site_stats` SET ss_total_edits=ss_total_edits+N
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
DatabaseBase::query: Writes done: REPLACE INTO `searchindex` (si_page,si_title,si_text) VALUES ('X')
BacklinkCache::partition: got from full result cache
BacklinkCache::queryLinks: got results from DB
BacklinkCache::partition: got from full result cache
Request ended normally


Start request GET /wiki/WPD:Infrastructure/architecture/VM_roles
HTTP HEADERS:
HOST: docs.webplatform.org
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=WPD:Infrastructure/architecture/VM_roles&action=edit
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
FASTLY-CLIENT-IP: 173.178.131.111
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.111, 173.178.131.111
COOKIE: wpwikiLoggedOut=1424902515; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06
X-VARNISH: 3880592861, 3181312243
ACCEPT-ENCODING: gzip
FASTLY-CLIENT: 1
X-FORWARDED-FOR: 173.178.131.111, 173.178.131.111
FASTLY-FF: cache-iad2130-IAD, cache-iad2131-IAD
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
User: cache miss for user 10080
User: loading options for user 10080 from database.
User: logged in from session
User: loading options for user 10080 from override cache.
MessageCache::load: Loading en... got from global cache
OutputPage::checkLastModified: client did not send If-Modified-Since header
Article::view using parser cache: yes
Parser options key expired, touched 20150225225559, epoch 20150225172757, cached 20150225225555
Article::view: doing uncached parse
Parser cache options found.
Unstubbing $wgParser on call of $wgParser::parse from WikitextContent::fillParserOutput
Parser: using preprocessor: Preprocessor_DOM
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:116c0786d3818b164345ef695ebc2196:1)
Pulling file metadata from cache key wpwiki:file:83bf02230c13678a2e84aed806cc506b
MimeMagic::__construct: loading mime types from /srv/webplatform/wiki/wpwiki/mediawiki/includes/mime.types
MimeMagic::__construct: loading mime info from /srv/webplatform/wiki/wpwiki/mediawiki/includes/mime.info
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
FileBackendStore::getFileStat: File mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png does not exist.
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_3f643b418320-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_658641ce3075-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
File::transform: Doing stat for mwstore://local-ceph/local-thumb/8/83/Component-diagram-internal.png/1624px-Component-diagram-internal.png
BitmapHandler::doTransform: creating 1624x841 thumbnail at /tmp/transform_f85ce5bfbd99-1.png using scaler im
BitmapHandler::doTransform: returning unscaled image
[Preprocessor] Loaded preprocessor XML from memcached (key wpwiki:preprocess-xml:7a0fc0b889a3183dc9963db86fea7ee2:0)
Unstubbing $wgLang on call of $wgLang::getCode from Message::inLanguage
Saved in parser cache with key wpwiki:pcache:idhash:58597-0!*!0!!*!2!*!esi=1 and timestamp 20150225225556 and revision id 100865
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[WPD:Infrastructure/architecture/VM roles]] are {edit,move}
OutputPage::sendCacheControl: private caching; Wed, 25 Feb 2015 22:56:00 GMT **
Request ended normally
</SyntaxHighlight>


=== Go to Main Page ===
==== Without Fastly ====
<syntaxHighlight lang="text">
Start request GET /wiki/Main_Page
HTTP HEADERS:
HOST: docs.webplatform.org
CONNECTION: keep-alive
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/wiki/WPD:Infrastructure/architecture/VM_roles
ACCEPT-ENCODING: gzip, deflate, sdch
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: _pk_ref.1.6aa5=%5B%22%22%2C%22%22%2C1424138557%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FPublic%2Fpublic-webplatform%2F2015Feb%2F0003.html%22%5D; _pk_id.1.6aa5=f60e7f3954913aa0.1420732750.108.1424138557.1424116005.; _pk_ref.9.6aa5=%5B%22%22%2C%22%22%2C1424182609%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FTeam%2Fw3t-sys%2F2015JanFeb%2F0093.html%22%5D; _pk_id.9.6aa5=ea6c3462853cd2d6.1421114716.7.1424182620.1422055058.; wptestwiki_session=37ad13fe80ea727fdbb89a1870dbb29c; wptestwikiUserID=150; wptestwikiUserName=Renoirb; _pk_ref.1.db2a=%5B%22%22%2C%22%22%2C1424897026%2C%22http%3A%2F%2Fwww.baidu.com%2Fs%3Fwd%3Dhtml%7Btouch-action%3Anone%3B%7D%22%5D; wpwikiLoggedOut=1424900841; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=dcdcmaq5g1d067e87sr2beslr7; _pk_id.1.db2a=e07e1a4d4c024be6.1424134581.36.1424901013.1424887118.; _pk_ses.1.db2a=*
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
User: got user 10080 from cache
User: loading options for user 10080 from override cache.
User: logged in from session
User: loading options for user 10080 from override cache.
MessageCache::load: Loading en... got from global cache
OutputPage::checkLastModified: client did not send If-Modified-Since header
Article::view using parser cache: yes
Parser cache options found.
ParserOutput cache found.
Article::view: showing parser cache contents
Unstubbing $wgLang on call of $wgLang::getCode from ParserOutput::replaceEditSectionLinksCallback
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
OutputPage::sendCacheControl: private caching; Wed, 25 Feb 2015 21:50:16 GMT **
Request ended normally
</syntaxHighlight>

==== With Fastly ====
<SyntaxHighlight  lang="text">
Start request GET /wiki/Main_Page
HTTP HEADERS:
HOST: docs.webplatform.org
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/wiki/WPD:Infrastructure/architecture/VM_roles
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
FASTLY-CLIENT-IP: 173.178.131.111
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.111, 173.178.131.111
COOKIE: wpwikiLoggedOut=1424902515; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06
X-VARNISH: 1858527122, 805532583
ACCEPT-ENCODING: gzip
FASTLY-CLIENT: 1
X-FORWARDED-FOR: 173.178.131.111, 173.178.131.111
FASTLY-FF: cache-jfk1023-JFK, cache-jfk1032-JFK
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
User: got user 10080 from cache
User: loading options for user 10080 from override cache.
User: logged in from session
User: loading options for user 10080 from override cache.
MessageCache::load: Loading en... got from global cache
OutputPage::checkLastModified: client did not send If-Modified-Since header
Article::view using parser cache: yes
Parser cache options found.
ParserOutput cache found.
Article::view: showing parser cache contents
Unstubbing $wgLang on call of $wgLang::getCode from ParserOutput::replaceEditSectionLinksCallback
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
OutputPage::sendCacheControl: private caching; Wed, 25 Feb 2015 22:56:00 GMT **
Request ended normally
</SyntaxHighlight>


=== Logout ===
==== Without Fastly ====
<syntaxHighlight lang="text">
Start request GET /w/index.php?title=Special:UserLogout&returnto=Main+Page
HTTP HEADERS:
HOST: docs.webplatform.org
CONNECTION: keep-alive
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/wiki/Main_Page
ACCEPT-ENCODING: gzip, deflate, sdch
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: _pk_ref.1.6aa5=%5B%22%22%2C%22%22%2C1424138557%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FPublic%2Fpublic-webplatform%2F2015Feb%2F0003.html%22%5D; _pk_id.1.6aa5=f60e7f3954913aa0.1420732750.108.1424138557.1424116005.; _pk_ref.9.6aa5=%5B%22%22%2C%22%22%2C1424182609%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FTeam%2Fw3t-sys%2F2015JanFeb%2F0093.html%22%5D; _pk_id.9.6aa5=ea6c3462853cd2d6.1421114716.7.1424182620.1422055058.; wptestwiki_session=37ad13fe80ea727fdbb89a1870dbb29c; wptestwikiUserID=150; wptestwikiUserName=Renoirb; _pk_ref.1.db2a=%5B%22%22%2C%22%22%2C1424897026%2C%22http%3A%2F%2Fwww.baidu.com%2Fs%3Fwd%3Dhtml%7Btouch-action%3Anone%3B%7D%22%5D; wpwikiLoggedOut=1424900841; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=dcdcmaq5g1d067e87sr2beslr7; _pk_id.1.db2a=e07e1a4d4c024be6.1424134581.36.1424901018.1424887118.; _pk_ses.1.db2a=*
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
User: got user 10080 from cache
User: loading options for user 10080 from override cache.
User: logged in from session
User: loading options for user 10080 from override cache.
MessageCache::load: Loading en... got from global cache
[cookie] setcookie: "wpwikiUserID", "", "1424814620", "/", "", "1", "1"
[cookie] setcookie: "wpwikiToken", "", "1424814620", "/", "", "1", "1"
[cookie] setcookie: "forceHTTPS", "", "1424814620", "/", "", "", "1"
[cookie] setcookie: "wpwikiLoggedOut", "1424901020", "1424987420", "/", "", "1", "1"
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Unstubbing $wgLang on call of $wgLang::_unstub from ParserOptions::__construct
IP: 173.178.131.111
OutputPage::sendCacheControl: private caching;  **
Request ended normally


Start request GET /wiki/Main_Page
HTTP HEADERS:
HOST: docs.webplatform.org
CONNECTION: keep-alive
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=Special:UserLogout&returnto=Main+Page
ACCEPT-ENCODING: gzip, deflate, sdch
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: _pk_ref.1.6aa5=%5B%22%22%2C%22%22%2C1424138557%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FPublic%2Fpublic-webplatform%2F2015Feb%2F0003.html%22%5D; _pk_id.1.6aa5=f60e7f3954913aa0.1420732750.108.1424138557.1424116005.; _pk_ref.9.6aa5=%5B%22%22%2C%22%22%2C1424182609%2C%22https%3A%2F%2Flists.w3.org%2FArchives%2FTeam%2Fw3t-sys%2F2015JanFeb%2F0093.html%22%5D; _pk_id.9.6aa5=ea6c3462853cd2d6.1421114716.7.1424182620.1422055058.; wptestwiki_session=37ad13fe80ea727fdbb89a1870dbb29c; wptestwikiUserID=150; wptestwikiUserName=Renoirb; _pk_ref.1.db2a=%5B%22%22%2C%22%22%2C1424897026%2C%22http%3A%2F%2Fwww.baidu.com%2Fs%3Fwd%3Dhtml%7Btouch-action%3Anone%3B%7D%22%5D; wpwikiUserName=Renoirb; wpwiki_session=dcdcmaq5g1d067e87sr2beslr7; wpwikiLoggedOut=1424901020; _pk_id.1.db2a=e07e1a4d4c024be6.1424134581.36.1424901022.1424887118.; _pk_ses.1.db2a=*
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
MessageCache::load: Loading en... got from global cache
OutputPage::checkLastModified: client did not send If-Modified-Since header
Article::view using parser cache: yes
Parser cache options found.
ParserOutput cache found.
Article::view: showing parser cache contents
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Unstubbing $wgLang on call of $wgLang::getCode from MessageCache::getMessageFromFallbackChain
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
IP: 173.178.131.111
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
OutputPage::sendCacheControl: private caching; Wed, 25 Feb 2015 21:50:20 GMT **
Request ended normally
</syntaxHighlight>

==== With Fastly ====
<SyntaxHighlight  lang="text">
Start request GET /w/index.php?title=Special:UserLogout&returnto=Main+Page
HTTP HEADERS:
HOST: docs.webplatform.org
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/wiki/Main_Page
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
COOKIE: wpwikiLoggedOut=1424902515; wpwikiUserID=10080; wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06; _pk_id.1.db2a=29c40a6dea503cbe.1424901216.1.1424905230.1424901216.; _pk_ses.1.db2a=*
FASTLY-CLIENT-IP: 173.178.131.111
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.111, 173.178.131.111
X-VARNISH: 1409429639, 1608044916
ACCEPT-ENCODING: gzip
FASTLY-CLIENT: 1
X-FORWARDED-FOR: 173.178.131.111, 173.178.131.111
FASTLY-FF: cache-jfk1026-JFK, cache-jfk1025-JFK
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
User: got user 10080 from cache
Connected to database 0 at 10.0.0.29
User: loading options for user 10080 from override cache.
User: logged in from session
User: loading options for user 10080 from override cache.
MessageCache::load: Loading en... got from global cache
[cookie] setcookie: "wpwikiUserID", "", "1424818845", "/", "", "", "1"
[cookie] setcookie: "wpwikiToken", "", "1424818845", "/", "", "", "1"
[cookie] setcookie: "forceHTTPS", "", "1424818845", "/", "", "", "1"
[cookie] setcookie: "wpwikiLoggedOut", "1424905245", "1424991645", "/", "", "", "1"
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Unstubbing $wgLang on call of $wgLang::_unstub from ParserOptions::__construct
IP: 173.178.131.111
OutputPage::sendCacheControl: private caching;  **
Request ended normally


Start request GET /wiki/Main_Page
HTTP HEADERS:
HOST: docs.webplatform.org
ACCEPT: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
USER-AGENT: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.115 Safari/537.36
DNT: 1
REFERER: https://docs.webplatform.org/w/index.php?title=Special:UserLogout&returnto=Main+Page
ACCEPT-LANGUAGE: fr-CA,fr;q=0.8,fr-FR;q=0.6,en-US;q=0.4,en;q=0.2
FASTLY-CLIENT-IP: 173.178.131.111
X-FORWARDED-HOST: docs.webplatform.org
X-FORWARDED-SERVER: www.webplatform.org
FASTLY-SSL: 1
FASTLY-TEMP-XFF: 173.178.131.111, 173.178.131.111
COOKIE: wpwikiUserName=Renoirb; wpwiki_session=bc1ec4fbf11d31c6907ceb23b70f2d06; wpwikiLoggedOut=1424905245
X-VARNISH: 2542060989, 805857636
ACCEPT-ENCODING: gzip
FASTLY-CLIENT: 1
X-FORWARDED-FOR: 173.178.131.111, 173.178.131.111
FASTLY-FF: cache-jfk1020-JFK, cache-jfk1032-JFK
[caches] main: MemcachedPeclBagOStuff, message: MemcachedPeclBagOStuff, parser: MemcachedPeclBagOStuff
[caches] LocalisationCache: using store LCStoreDB
Fully initialised
Connected to database 0 at 10.0.0.29
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
[ContentHandler] Created handler for wikitext: WikitextContentHandler
IP: 173.178.131.111
MessageCache::load: Loading en... got from global cache
OutputPage::checkLastModified: client did not send If-Modified-Since header
Article::view using parser cache: yes
Parser cache options found.
ParserOutput cache found.
Article::view: showing parser cache contents
[deprecated] Use of wfMsg was deprecated in MediaWiki 1.21. [Called from wfEditSectionLinkTransform in /srv/webplatform/wiki/wpwiki/mediawiki/extensions/WebPlatformDocs/extensions/EditSectionIcon.php at line 26]
[deprecated] Use of wfMsgReal was deprecated in MediaWiki 1.21. [Called from wfMsg in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1498]
[deprecated] Use of wfMsgGetKey was deprecated in MediaWiki 1.21. [Called from wfMsgReal in /srv/webplatform/wiki/wpwiki/mediawiki/includes/GlobalFunctions.php at line 1596]
Unstubbing $wgLang on call of $wgLang::getCode from MessageCache::getMessageFromFallbackChain
Unstubbing $wgParser on call of $wgParser::firstCallInit from MessageCache::getParser
Parser: using preprocessor: Preprocessor_DOM
Title::getRestrictionTypes: applicable restrictions to [[Main Page]] are {edit,move}
OutputPage::sendCacheControl: private caching; Wed, 25 Feb 2015 23:00:45 GMT **
Request ended normally
</SyntaxHighlight>