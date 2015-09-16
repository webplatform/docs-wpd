---
title: Login workflows
uri: 'WPD:Projects/SSO/Login Workflows'

---
Both of these scenarios assume that the Annotator sidebar is loaded on the target page load via an explicit script reference; both use the same instance of Hypothes.is Annotator, hosted on WebPlatform.org (specifically, notes.webplatform.org).

## User facing

### WebPlatform.org

1.  User arrives on content page *X* on WebPlatform.org
    -   User wishes to edit or annotate page

2.  User clicks login link
    -   Main login link on top of wiki page
    -   Optional login link in Annotator sidebar

3.  User navigated to login page on WebPlatform.org (accounts.webplatform.org, using FxA)
4.  User logs in via FxA
5.  User redirected back to content page *X*
6.  MediaWiki and Annotator both reloaded with user logged in via authentication token
    -   Option 1: MediaWiki and Annotator both use token from FxA
    -   Option 2: MediaWiki uses token from FxA, and Annotator uses token from MediaWiki

7.  User now able to edit wiki or leave annotation

No popup needed?

### W3C Specs

1.  User arrives on specification page *Y* on W3.org
    -   User wishes to annotate specification

2.  User clicks login link in Annotator sidebar
3.  User logs in with WebPlatform.org account through the Annotator sidebar
    -   If browser has cross-site cookies enabled, user logs in directly in sidebar
    -   If browser does not have cross-site cookies enabled, user logs in via a pop-up dialog

4.  Annotator sidebar obtains authentication token from accounts.webplatform.org, using FxA
5.  Sidebar reloaded?
6.  User now able to annotate specification page *Y*

Popup may be needed?

## How the code has to behave

### Functionnal workflows

Those are the functional requirements to enable SSO. Each workflow is detailed in [WPD:Projects/SSO/How we implemented it](/WPD:Projects/SSO/How_we_implemented_it)

In order to fulfill the given [WPD:Projects/SSO/How we implemented it\#Stories](/WPD:Projects/SSO/How_we_implemented_it#Stories) and workflows, we needed to implement a SSO solution covers the following:

-   Get authenticated through a single authority (see [WPD:Projects/SSO/How we implemented it\#Delegating authentication](/WPD:Projects/SSO/How_we_implemented_it#Delegating_authentication))
-   [WPD:Projects/SSO/How we implemented it\#Read user data](/WPD:Projects/SSO/How_we_implemented_it#Read_user_data) from an API,
-   Let each configured web applications to detect a session on the authority (see [WPD:Projects/SSO/How we implemented it\#SSO and remembering](/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering))
-   handle their local users and session (see [WPD:Projects/SSO/How we implemented it\#Initialize local web application session](/WPD:Projects/SSO/How_we_implemented_it#Initialize_local_web_application_session)), and
-   Detect automatically if there is a session in the accounts server, and start it automatically (see [[[WPD:Projects/SSO/How we implemented it\#JavaScript shared module: Detect and start automatically a session](/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session))

### Starting a session by communicating with accounts server

This section covers what the *front-end* does to detect if a session is opened on the accounts server. To see the *back-end* part, refer to [WPD:Projects/SSO/How we implemented it\#1.2 Possibility: Resuming a session confirmed by the accounts server](/WPD:Projects/SSO/How_we_implemented_it#1.2_Possibility:_Resuming_a_session_confirmed_by_the_accounts_server), detailed in the section [WPD:Projects/SSO/How we implemented it\#SSO and remembering](/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering)

-   In the accounts server:
    -   Accept framing (i.e. accept to create iframe from other domain names that we control) through appropriate CSP policies.
    -   Create an event handler that replies with a JSON object that reads the sessionToken in current localStorage. (Note that in the returned object, we rename the key *sessionToken* to *recoveryPayload*) (e.g. `{recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f", hasSession: true}`)
-   Through JavaScript, on a web application relying on the SSO (details in [WPD:Projects/SSO/How we implemented it\#JavaScript shared module: Detect and start automatically a session](/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session)):
    -   Check if web application has a session locally, if not, continue
    -   Create a communication channel as an hidden iframe, if the accounts server doesn’t forbid due to CSP policy, continue.
    -   Use `postMessage` to communicate through the iframe opened to the accounts server
    -   Handle response from `postMessage`, use the returned data (i.e. `sessionToken` value) into a POST body member called "recoveryPayload"
    -   Make a `POST` request to the current web app callback (e.g. `/wiki/Special:AccountsHandler/callback`) with "recoveryPayload"
-   In the backend code (details in [WPD:Projects/SSO/How we implemented it\#Initialize local web application session](/WPD:Projects/SSO/How_we_implemented_it#Initialize_local_web_application_session)):
    -   Accept `POST` requests with a "recoveryPayload" parameter, make sure it’s 64 hexadecimal characters.
    -   Rename the "recoveryPayload" as "sessionToken"
    -   Make an off-the-band call over SSL to the profile server
    -   Read a JSON object with the user data
    -   Create a session without further validation
    -   Return an HTTP status code: `204` if it worked, `4xx` if it didn’t, `5xx` if an unexpected backend error happened. (see [WPD:Projects/SSO/How we implemented it\#1.2.4 Return an HTTP response](/WPD:Projects/SSO/How_we_implemented_it#1.2.4_Return_an_HTTP_response))

**NOTE**: This workflow is subject to change, the details is described in [WPD:Projects/SSO/Improvements roadmap\#Recovering session data](/WPD:Projects/SSO/Improvements_roadmap#Recovering_session_data).

## Reference

-   [Sessions and authentication](http://www.whatcodecraves.com/posts/2012/01/11/backbonejs-sessions-and-authentication) describes how a session works, you can ignore what is specific to backbone.
