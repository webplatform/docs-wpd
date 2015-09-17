---
title: 'Improvements roadmap'
uri: 'WPD:Projects/SSO/Improvements roadmap'

---
The steps described in [WPD:Projects/SSO/How we implemented it](/WPD:Projects/SSO/How_we_implemented_it) can be improved, this page describes some proposals.

## Recovering session data

This change proposal is about making sure the exchanged information is encoded in ways that only the intended audience can use.

### Problem in the original steps

ANYBODY who got access to a sessionToken, could become that user. And that is as long as the victim keeps his session opened on the accounts server. Because there is no way to validate if the request is made from the legitimate user.

This security issue is no different than any web application that doesn’t use SSL. After all, the way a web server has to differentiate a visitor from another is basically a set of cookies, one of them serves as a session token.

One obvious solution is to have SSL across the whole site, but its not always possible. We cannot force the user to go back and forth from SSL if they are OK without it. But we cannot leave such powerful data without encoding it either.

### Proposed solution steps

To solve the possible exploit, let’s revisit the original steps described in [WPD:Projects/SSO/Login Workflows\#Starting a session by communicating with accounts server](/WPD:Projects/SSO/Login_Workflows#Starting_a_session_by_communicating_with_accounts_server). Differences are shown in **bold**, removed steps has been ~~crossed out~~.

-   In the accounts server:
    -   **Add a wrapper within FxA server node processes (i.e. not possible to call from the browser), make sure the wrapper module isn’t going to be publicly available (e.g. in a secret project in Gerrit), to manage the encoding** (\#TODO)
    -   **Encode the sessionToken in some way with a shared secret key (e.g. using AES)**
    -   **Save the encoded sessionToken in a LocalStorage variable "`recoveryPayload`", but instead of a 64 characters long HEX string, `recoveryPayload` will a JSON object (e.g. `{recoveryPayload: {packet: "...", cipherId: 1}}`)**
    -   Accept framing (i.e. accept to create iframe from other domain names that we control) through appropriate CSP policies.
    -   ~~Create an event handler that replies with a JSON object that reads the sessionToken in current localStorage. (Note that in the returned object, we rename the key *sessionToken* to *recoveryPayload*) (e.g. `{recoveryPayload: "e73f75c00115f45416b121e274fd77b60376ce4084267ed76ce3ec7c0a9f4f1f", hasSession: true}`)~~
    -   **Create an event handler that replies with a JSON object that reads the current `recoveryPayload` value in localStorage.**
-   Through JavaScript, on a web application relying on the SSO (details in [WPD:Projects/SSO/How we implemented it\#JavaScript shared module: Detect and start automatically a session](/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session)):
    -   Check if web application has a session locally, if not, continue
    -   Create a communication channel as an hidden iframe, if the accounts server doesn’t forbid due to CSP policy, continue.
    -   Use `postMessage` to communicate through the iframe opened to the accounts server
    -   Handle response from `postMessage`, use the returned data (i.e. ~~`sessionToken`~~ **`recoveryPayload`** value) into a POST body member called "recoveryPayload"
    -   Make a `POST` request to the current web app callback (e.g. `/wiki/Special:AccountsHandler/callback`) with "recoveryPayload" **that has to get url encoded**
-   In the backend code (details in [WPD:Projects/SSO/How we implemented it\#Initialize local web application session](/WPD:Projects/SSO/How_we_implemented_it#Initialize_local_web_application_session)):
    -   Accept `POST` requests with a "recoveryPayload" parameter~~, make sure it’s 64 hexadecimal characters~~
    -   ~~Rename the "recoveryPayload" as "sessionToken"~~
    -   **Decode the urlencoded "recoveryPayload" blob, then unpack the data using the shared secret key. If the payload makes any sense, has a property called "sessionToken", continue**
    -   **If the sessionToken property is 64 hexadecimal characters, use it for the next step**
    -   Make an off-the-band call over SSL to the profile server
    -   Read a JSON object with the user data
    -   Create a session without further validation
    -   Return an HTTP status code: `204` if it worked, `4xx` if it didn’t, `5xx` if an unexpected backend error happened. (see [WPD:Projects/SSO/How we implemented it\#1.2.4 Return an HTTP response](/WPD:Projects/SSO/How_we_implemented_it#1.2.4_Return_an_HTTP_response))

**Pros**:

-   Only the encoded packet will be communicated across frames
-   If a relying party doesn’t use SSL, the data will need to be decoded to be useful
-   Whether or not the session had a "man in the middle", the attacker will
    -   The used crypto cipher is not explicitly communicated in the process, only a "cypherId" number
    -   Still need to get the secret key —that is NEVER communicated in the process— to unpack the encoded "recoveryPayload" contents.
    -   not get a chance to get anything useful from the JavaScript call to the call back GET parameters
-   Each backend application will have to unpack the recoveryPayload, validate if it makes sense BEFORE communicating with the profile.accounts.webplatform.org endpoint.

**What we could add on top of it**:

-   Sign the response from the profile server using JWT format, see [jwcrypto](https://github.com/mozilla/jwcrypto)
-   Validate on the backend whether the response from the profile server is valid
-   Have SSL everywhere

## Leveraging completely OAuth2

The current implementation described at [WPD:Projects/SSO/How we implemented it\#SSO and remembering](/WPD:Projects/SSO/How_we_implemented_it#SSO_and_remembering) doesn’t use OAuth2 token in all communications. While the original design of Firefox Accounts OAuth server was to remember if a user previously authenticated, that functionality is not implemented yet.

The issue is known and documented [in their GitHub issue tracker \#1195](https://github.com/mozilla/fxa-content-server/issues/1195).

In the eventuality of the Firefox Accounts OAuth server changes its behavior, we still need a non-blocking [WPD:Projects/SSO/How we implemented it\#JavaScript shared module: Detect and start automatically a session](/WPD:Projects/SSO/How_we_implemented_it#JavaScript_shared_module:_Detect_and_start_automatically_a_session) to check whether a session is already opened.

### Proposed solution

TBD
