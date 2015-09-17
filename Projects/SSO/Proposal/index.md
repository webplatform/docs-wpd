---
title: 'Proposal'
uri: 'WPD:Projects/SSO/Proposal'

---
## Goals

-   Annotation on WPD by signing into MW
-   Annotation on specs, using WPD account, without a pop-up
-   Use same account on various WPD web applications (i.e. test wiki, issue tracker, blog, etc)

## Known limitations

-   Users who opt-in to third-party cookie blocking cannot log in from the sidebar if it is served from its own domain
    -   Safari blocks third-party cookies by default

The hypothes.is Chrome extension requests permissions at install time to modify browser settings. Then it whitelists the Hypothes.is domain as a third-party cookie exception. This option is unavailable for the case of embedding the application directly.

## Possibilities

### WPD

1.  No authentication UI in the sidebar. All authentication is done in MW. Hypothesis produces a plugin for the annotation sidebar which sniffs the MW authentication.

### Specs

1.  Authentication in the sidebar against MW API. Requires domain to be www.w3.org
2.  Authentication in the sidebar against FxA OAuth API\*.

The domain must be www.w3.org or the FxA OAuth server.

## Questions

Can we add reverse proxy routes for /notes on www.w3.org and wpd such that the iframe is always same domain? Our backend has no trouble with being served from two domains at once. This would be the simplest route because it means we can leave authentication in the sidebar for specs.

Example:

-   w3.org/notes
-   webplatform.org/notes

## Proposal

-   Hypothesis develops MW authentication
    -   Front end: sniff the MW auth (used for WPD)
    -   Back end: username/password auth against MW API (used for specs)
-   W3C continues to roll out FxA
-   We choose a hard stop date. If FxA is deployed by then, Hypothesis develops a back end which authentications username/password against FxA.

**We will have pop-ups** on spec pages unless we put Hypothesis and MW (or FxA) on the same domain. Switching to FxA/OAuth does not change this.

## Estimates

-   **MediaWiki front-end authentication sniffing:** 1-2 days
-   **MediaWiki back-end authentication interop:** 1-2 days
-   **FxA back-end authentication interop:** 2-3 days
-   **FxA roll-out:** ????? (Renoir?)

I propose a hard stop for FxA roll-out at Monday, May 26th. That gives Hypothesis the next week to focus intensely on IE11 support and a solid week for authentication work against either FxA or MW, with a few days left over for testing the deployment and time dilation.
