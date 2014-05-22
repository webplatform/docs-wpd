== Adapt Firefox Accounts for WebPlatform ==

=== Summary ===

Firefox Accounts ("FxA") is an Identity Provider system made by Mozilla that has been rolled out with Firefox 29. It will eventually be the centerpiece for their Marketplace and other services, the first components are about authentication, and Resource Provider using both OAuth2[6] and Hawk[5] —a fork from OAuth 1, for internal use but also accessible.

FxA is using JavaScript for all parts of the project. It uses multiple components and talks through APIs. It has [https://github.com/webplatform/fxa-js-client a javascript client ("fxa-js-client")], a [https://github.com/webplatform/fxa-content-server Content server ("fxa-content-server")] that’s taking care of the Web UI and also provide email content templates. The Content server also [https://github.com/webplatform/fxa-content-server-l10n supports Localization ("fxa-content-server-l10n")] allowing us to support multi-lingual content. In the backend side, FxA exposes [https://github.com/webplatform/fxa-auth-server an API ("fxa-auth-server")], and last but not least, an [https://github.com/webplatform/fxa-oauth-server OAuth2 resource provider ("fxa-oauth-server")].

Our use of FxA will be limited to a minimum to suit our needs. In the future, we might consider using other components managed by the FxA community, such as:  [https://github.com/mozilla/fxa-customs-server customs-server] that’s taking care to validate emails, manage bounces and help prevent spam, and also [https://github.com/mozilla/fxa-auth-db-server auth-db-server] that will provide a REST/HTTP frontend to the database servers, and many other components.

WebPlatform Docs is using its own fork of FxA to serve as a SSO and this document describes the changes that has been made to it.

The choice of using FxA for our authentication service is due to our interest to limit our technology stack as much as its sane to do so. JavaScript is a sensible choice to us, and we found that FxA also leverage respected quality practices and modern industry practices (e.g. Hawk, OAuth, Bower, Tests, etc) and maintained by an active community.

=== Components ===

We are currently forking the following components based on recommended version/tags from the Mozilla fxa group.


* [https://github.com/webplatform/fxa-content-server fxa-content-server], using branch train-12.
* [https://github.com/webplatform/fxa-content-server-l10n fxa-content-server-l10n], adjusting content based off of train-12
* [https://github.com/webplatform/fxa-js-client fxa-js-client], that is installed within fxa-content-server via the bower.json file.
* [https://github.com/webplatform/fxa-auth-server fxa-auth-server]
* [https://github.com/webplatform/fxa-oauth-server fxa-oauth-server]