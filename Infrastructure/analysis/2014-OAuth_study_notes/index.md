= OAuth Study notes =

See [http://notes.webplatform.org/stream?tags=gist-9837155 annotations thread]

== What is OAuth? ==

OAuth is a way to validate authenticity between various players in the context of multiple application communicating together. It is a framework to validate the rights ("Grant") and how to  request for information from one system to another.

It is similar to what a ''Valet-key'' of a car is for:
> Many luxury cars come with a valet key. It is a special key you give the parking attendant and unlike your regular key, will only allow the car to be driven a short distance while blocking access to the trunk (...).
source (link10)

OAuth is not the first attempt to solve the authentication. There were also OpenID, and SAML, both are older and besides the fact that OAuth is younger, it can do more. 

While OpenID was about keeping authorization and user information. It doesn’t solve the problem that third parties has to create a local account with the user. That's where OAuth comes in to play.

* Giving access tokens to consumers without giving away private information<br />
* Setting ''rules'' for sharing information through APIs
* Keywords:
** '''Service provider''': It is understood that this is used when an entity serves both as: Resource Server, and Authorization server in the transparently.
** '''Resource server''': The API; (''synonyms'': RS)
** '''Authorization server''': The system to login against; (''synonyms'': AS)
** '''Consumer''': 3rd party looking to receive data. (external site, mobile app, etc)
** '''User''': A human being (''synonyms'': Ressource owner)
** '''Scope''': Expressed in non standardized ways, to convey what can be done. (''synonyms'': entitlement)
** '''Grant''': Many types, depending of the use-case (term used in the documentation): Web-server app (authorization_code), Browser-based app (implicit), Username/password (password), Mobile apps (implicit), Authorization code, and Extension grant (how you would wire a SAML in the process) see (link9)
* To serve as a way to certify what is allowed to be done, before doing it. The part that is describing is referred to as "Scope" or "Entitlement" (link2)
* Ways to describe Scope/entitlement spec leaves it open ended. In the article (link2) they show various ways used by know websites.

=== In other words ===

<blockquote>
The client application obtains a token (with user consent) with which the client application can act on behalf of a user. Note the important distinction: the application does not become the user. The application is simply able to indicate that it is acting on behalf of a user for a particular scope of activity.
</blockquote>
[http://notes.webplatform.org/a/D3xZP4xeTpiKDFHD_IGrFA annotation], source: (link6)


=== Compared to SAML ===
Both address the same problem, besides the fact that SAML is dating from 2005 and serves only to web applications. In other words, due to SAML design, a native mobile application cannot use it. Because back in 2005, nobody could expect the mobile bubble and the information exchange mechanism requires things that cannot be achieved.


-----

== Flow ==

Quoting the example given in (link8)

[[File:mutuallyhuman-com-strategy-sso-schema-oauth2-flow.png]]

<blockquote>
* (A) -- a user opens their web-browser and goes to MyPhotos.com which stores all of their photos. MyPhotos.com doesn't handle authentication itself, so the user is redirected to the Authorization Server with a request for authorization. The user is presented with a login form and is asked if they want to approve the Resource Server (MyPhotos.com) to act on their behalf. The user logs in and they are redirected back to MyPhotos.com.
* (B) -- MyPhotos.com receives an authorization grant code as a part of the redirect and then passes this along to the client.<br />
* (C) -- the Client then uses that authorization grant code to request an access token from the Authorization Server.<br />
* (D) -- if the authorization grant code is valid, then the Authorization Server grants an access token. The access token is then used by the client to request resources from the Resource Server (MyPhotos.com).<br />
* (E) -- MyPhotos.com receives the request for a resource and it receives the access token. In order to make sure it's a valid access token it sends the token directly to the Authorization Server to validate. If valid, the Authorization Server sends back information about the user.<br />
* (F) -- having validated the user's request MyPhotos.com sends the requested resource back to the user.
</blockquote>

-----

== Facts ==

=== Scope ===

Has to be created and enforced among the ecosystem of the OAuth Service provider.

For example, when somebody use Twitter as OAuth Service provider, the Consumer can do things that Twitter's scope is allowing. If we create our own OAuth, we have to set in place our ''own'' set of scopes.

Note:

* Some documentation also refer this component as an "Entitlement" (are they synonyms?)
* In SAML, they also have concept of Tokens, but document how to represent it (link8)

'''In other words'''

<blockquote>(...) because OAuth uses both a client application credential (aka client identifier) and a token representing the user's scope of permission, service providers like banks, are able to set different access policies for client applications authorized by their customers.
</blockquote>
[http://notes.webplatform.org/a/cn5hB9q5SoC9BgnvmoKhdw annotation], source: (link6)

=== ''Service provider'', ''Resource Server'' and ''Authorization Server'' ===

There is more than one component

* Resource Server<br />
* Authorization server

Although most of the services expos them as one, they are functionally different and can be decoupled.

'''Synonyms''' (to validate)

* Service provider<br />
* Resource Server ("RS")
* Authorization Server "AS")

=== Tokens, and their lifetime ===

<blockquote>(...) OAuth uses a code/refresh token/access token system that enables 3 possible session lifetimes for a single relationship (...)

* '''When a user initially authorizes an application''' to have access, a code is issued (first lifetime). Typically this code is used one-time to obtain something called a refresh token or access token.<br />
* '''A refresh token''' (the second lifetime) is '''optional''', but the intention is that it is kept for a longer term and allows the client application to obtain resource access tokens. Refresh tokens might typically last days or months.<br />
* '''Resource access tokens''' (third lifetime) are then used (often as '''bearer tokens''') to access protected services. These tokens are typically short-lived (minutes/hours).
</blockquote>
source: (link6)

'''Synonyms''' (to validate)

* Bearer token<br />
* Token<br />
* Grant<br />
* OAuth Grant<br />
* Authorization

=== SAML vs OAuth ===

This article (link7) went through to compare the terminology and the description of both technologies.

<blockquote>''SAML'' and ''OAuth2'' use similar terms for similar concepts.

For comparison the formal SAML term is listed with the OAuth2 equivalent in parentheses.

* Service Provider (Resource Server) -- this is the web-server you are trying to access information on.
* Client -- this is how the user is interacting with the Resource Server, like a web app being served through a web browser.
* Identity Provider (Authorization Server) -- this is the server that owns the user identities and credentials. It's who the user actually authenticates with.
</blockquote>
source: (link7)

== And now, for WebPlatform Docs use-cases ==

* ''MediaWiki OAuth Extension'' on [https://github.com/wikimedia/mediawiki-extensions-OAuth github.com/wikimedia] repository and [https://git.wikimedia.org/tree/mediawiki%2Fextensions%2FOAuth the official Gerrit repo].


-----

== References ==

* (link1) [http://www.hongkiat.com/blog/oauth-connect/ Unofficial blog post about OAuth Connect]<br />
* (link2) [http://brandur.org/oauth-scope Unofficial blog post about OAuth Scope] (unofficial article)<br />
* (link4) [http://www.slideshare.net/travisspencer/calling-an-oauth-10a-api-from-an-oauth-20-api Slides about collaboration between multiple OAuth providers]<br />
* (link3) [https://developers.facebook.com/docs/facebook-login/permissions#permissions Facebook developer documentation: OAuth scope and permissions]<br />
* (link5) [https://dev.twitter.com/docs/auth/application-only-auth Twitter developer documentation: Application only auth]<br />
* (link6) [http://www.independentid.com/2010/12/oauth-more-than-just-delegation.html OAuth, more than just delegation]<br />
* (link7) [http://www.mutuallyhuman.com/blog/2013/05/09/choosing-an-sso-strategy-saml-vs-oauth2/ Choosing an SSO Strategy; OAuth vs SAML]<br />
* (link8) [http://en.wikipedia.org/wiki/Security_Assertion_Markup_Language#SAML_Assertions SAML Assertion and tokens]
* (link9) [http://tools.ietf.org/html/rfc6749#section-4.1 IETF OAuth spec, Grant types]
* (link10) [http://hueniverse.com/2010/05/introducing-oauth-2-0/  Introducting OAuth 2.0]