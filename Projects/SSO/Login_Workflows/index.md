= Login workflows =

Both of these scenarios assume that the Annotator sidebar is loaded on the target page load via an explicit script reference; both use the same instance of Hypothes.is Annotator, hosted on WebPlatform.org (specifically, notes.webplatform.org).

== User facing ==

=== WebPlatform.org ===

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


=== W3C Specs ===

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

== How the code has to behave ==

=== Functionnal workflows ===

Those are the functional requirements to enable SSO. Each workflow is detailed in [[WPD:Projects/SSO/How we implemented it]]

In order to fulfill the given [[WPD:Projects/SSO/How we implemented it#Stories]] and workflows, we needed to implement a SSO solution covers the following:

* Get authenticated through a single authority (see [[WPD:Projects/SSO/How we implemented it#Delegating authentication]])
* [[WPD:Projects/SSO/How we implemented it#Read user data]] from an API, 
* Let each configured web applications to detect a session on the authority (see [[WPD:Projects/SSO/How we implemented it#SSO and remembering]])
* handle their local users and session (see [[WPD:Projects/SSO/How we implemented it#Initialize local web application session]]), and
* Detect automatically if there is a session in the accounts server, and start it automatically (see [[[[WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session]])


=== Starting a session by communicating with accounts server ===

This section covers what the ''front-end'' does to detect if a session is opened on the accounts server. To see the ''back-end'' part, refer to [[WPD:Projects/SSO/How we implemented it#1.2 Possibility: Resuming a session confirmed by the accounts server]], detailed in the section [[WPD:Projects/SSO/How we implemented it#SSO and remembering]]

* In the accounts server:
** Accept framing (i.e. accept to create iframe from other domain names that we control) through appropriate CSP policies.
** Create an event handler that replies with a JSON object that reads the current sessionToken in SessionStorage (e.g. <tt>{sessionToken: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f"}</tt>)
* Through JavaScript, on a web application relying on the SSO (details in [[WPD:Projects/SSO/How we implemented it#JavaScript shared module: Detect and start automatically a session]]):
** Check if web application has a session locally, if not, continue
** Create a communication channel as an hidden iframe, if the accounts server doesn’t forbid due to CSP policy, continue.
** Use <tt>postMessage</tt> to communicate through the iframe opened to the accounts server
** Handle response from <tt>postMessage</tt>, use the returned data (i.e. <tt>sessionToken</tt> value) into a POST body member called "recoveryPayload"
** Make a <tt>POST</tt> request to the current web app callback (e.g. <tt>/wiki/Special:AccountsHandler/callback</tt>) with "recoveryPayload"
* In the backend code (details in [[WPD:Projects/SSO/How we implemented it#Initialize local web application session]]):
** Accept <tt>POST</tt> requests with a "recoveryPayload" parameter, make sure it’s 64 hexadecimal characters.
** Rename the "recoveryPayload" as "sessionToken"
** Make an off-the-band call over SSL to the profile server
** Read a JSON object with the user data
** Create a session without further validation
** Return an HTTP status code: <tt>204</tt> if it worked, <tt>4xx</tt> if it didn’t, <tt>5xx</tt> if an unexpected backend error happened.

'''NOTE''': This workflow is subject to change, the details is described in [[WPD:Projects/SSO/Improvements roadmap#Recovering session data]].