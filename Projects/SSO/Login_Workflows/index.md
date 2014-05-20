Both of these scenarios assume that the Annotator sidebar is loaded on the target page load via an explicit script reference; both use the same instance of Hypothes.is Annotator, hosted on WebPlatform.org (specifically, notes.webplatform.org).

==WebPlatform.org==
# User arrives on content page ''X'' on WebPlatform.org
#* User wishes to edit or annotate page
# User clicks login link
#* Main login link on top of wiki page
#* Optional login link in Annotator sidebar
# User navigated to login page on WebPlatform.org (accounts.webplatform.org, using FxA)
# User logs in via FxA
# User redirected back to content page ''X''
# MediaWiki and Annotator both reloaded with user logged in via authentication token 
#* Option 1: MediaWiki and Annotator both use token from FxA
#* Option 2: MediaWiki uses token from FxA, and Annotator uses token from MediaWiki
# User now able to edit wiki or leave annotation

No popup needed?

==W3C Specs==
# User arrives on specification page ''Y'' on W3.org
#* User wishes to annotate specification
# User clicks login link in Annotator sidebar
# User logs in with WebPlatform.org account through the Annotator sidebar
#* If browser has cross-site cookies enabled, user logs in directly in sidebar 
#* If browser does not have cross-site cookies enabled, user logs in via a pop-up dialog
# Annotator sidebar obtains authentication token from accounts.webplatform.org, using FxA
# Sidebar reloaded?
# User now able to annotate specification page ''Y''

Popup may be needed?