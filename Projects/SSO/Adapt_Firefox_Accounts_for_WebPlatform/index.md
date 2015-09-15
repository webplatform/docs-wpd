---
title: Adapt Firefox Accounts for WebPlatform
uri: 'WPD:Projects/SSO/Adapt Firefox Accounts for WebPlatform'

---
## <span>Summary</span>

Firefox Accounts ("FxA") is an Identity Provider system made by Mozilla that has been rolled out with Firefox 29 released in May 2014. It will eventually be the centerpiece for their Marketplace and other services, the first components are about authentication, and to serve as a Resource Provider.

WebPlatform is using its own fork of FxA to serve as a SSO and this document describes the changes that has been made to it.

## <span>What is Firefox Accounts, and why?</span>

The choice of using FxA for our authentication service is due to our interest to limit our technology stack as much as its sane to do so. But FxA also supports other requirements we have, such as:

-   Use of JavaScript/NodeJS
-   Supports multiple languages
-   Maintained by an active community who also happens to be [one of our Stewards, Mozilla](http://www.webplatform.org/stewards/mozilla)

FxA provides has a set of loosely coupled components. Namely, a [JavaScript client ("fxa-js-client")](https://github.com/webplatform/fxa-js-client), a [Content server ("fxa-content-server")](https://github.com/webplatform/fxa-content-server) that’s taking care of the Web UI but also email templates. The Content server also [supports Localization ("fxa-content-server-l10n")](https://github.com/webplatform/fxa-content-server-l10n) allowing us to support multi-lingual content. In the backend side, FxA exposes [an API ("fxa-auth-server")](https://github.com/webplatform/fxa-auth-server), and last but not least, an [OAuth2 resource provider ("fxa-oauth-server")](https://github.com/webplatform/fxa-oauth-server).

Our use of FxA will be limited to a minimum to suit our needs. In the future, we might consider using other components managed by the FxA community, such as: [customs-server](https://github.com/mozilla/fxa-customs-server) that’s taking care to validate emails, manage bounces and help prevent spam, and also [auth-db-server](https://github.com/mozilla/fxa-auth-db-server) that will provide a REST/HTTP frontend to the database servers, and many other components available on [their GitHub projects](https://github.com/mozilla?query=fxa-).

## <span>Components</span>

We forked the following components based on recommended version/tags from the Mozilla fxa team.

-   [fxa-content-server](https://github.com/webplatform/fxa-content-server), using branch master
-   [fxa-content-server-l10n](https://github.com/webplatform/fxa-content-server-l10n), adjusting content based off of the same branch as fxa-content-server
-   [fxa-js-client](https://github.com/webplatform/fxa-js-client), that is installed within fxa-content-server via the bower.json file
-   [fxa-auth-server](https://github.com/webplatform/fxa-auth-server), branch webplatform-customizations
-   [fxa-oauth-server](https://github.com/webplatform/fxa-oauth-server)

## <span>Changes</span>

### <span>Accept username field, and allow to force creation date</span>

1.  Accept two fields [username, fullName] and allow forcing createdAt
    1.  [fxa-auth-server issue \#1](https://github.com/webplatform/fxa-auth-server/issues/1), patch [File:fxa-auth-server-patch-0001-Adressing-1-for-fxa-auth-server.txt](/File:fxa-auth-server-patch-0001-Adressing-1-for-fxa-auth-server.txt)
    2.  [fxa-js-client issue \#1](https://github.com/webplatform/fxa-js-client/issues/1)
    3.  [fxa-content-server issue \#1](https://github.com/webplatform/fxa-content-server/issues/1)

### <span>On login, also support using username instead of email</span>

**Status: In analysis**

The idea is that we would like to not change behavior for users when they login with their username.

**Limitations**

-   we do not want to change FxA too much (i.e. not break updates).
-   since the [way to validate user uses cryptography based on the email](https://github.com/mozilla/fxa-auth-server/wiki/onepw-protocol#login-obtaining-the-sessiontoken), we cannot just fake emails in the field, we will need it at many places such as confirming the user email and it would be a too big change

**Proposed solution**

Since we already implemented to accept username in [\#Accept username field, and allow to force creation date](#Accept_username_field.2C_and_allow_to_force_creation_date), we can create a set of API mirroring the original, but to find by username.

What we can do:

-   Create a distinct:
    -   login screen in content-server (e.g. /signin2) that shows username+password fields
    -   login API endpoint to api-server to accept those two fields
    -   Adjust API endpoint to use a different SELECT query to find user to make crypto checks. i.e. will continue as usual, but instead of searching user entry in database by provided email, we will allow to use username.
