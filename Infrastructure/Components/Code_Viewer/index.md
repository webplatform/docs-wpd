---
title: Code Viewer
uri: 'WPD:Infrastructure/Components/Code Viewer'

---
Among Web Platform Docs features is a live code viewer and pastebin. It allows us to keep in one place all code samples.

The webapp we are using for this is [Lea Verou](http://lea.verou.me)'s [Dabblet](http://dabblet.com/) available at [**code.webplatform.org**](http://code.webplatform.org/) and keeps the code in a [dedicated GitHub Gists repository](https://gist.github.com/WebPlatformDocs).

## <span>Features</span>

-   Provides a live preview of input HTML, CSS, SVG, JavaScript
-   Allows users to share code snippets with each other, as a pastebin *(mostly done, still replies on GitHub)*
-   Provides a way to open example code from the wiki in live example without copy-paste *(some progress, not done)*

## <span>Needs improvement</span>

-   Cannot work directly with raw HTML file and HTTP headers
-   Find way to add another file and define its content-type

## <span>Integration</span>

Because integration has many aspects, we will roll out full support for this feature in several steps.

### <span>Roadmap</span>

#### <span>Phase 1: Static Live Code Viewer</span>

**Status:** *Done*

#### <span>Phase 2: Open Examples from Wiki</span>

**Status:** *not started*

#### <span>Phase 3: Inline Live Examples</span>

**Status:** *not started*

#### <span>Phase 4: Host Gists on WebPlatform.org</span>

**Status:** *not started*

### <span>Other Tasks</span>

## <span>Technical Requirements</span>

### <span>Dedicated Subdomain</span>

The public URL will be [code.webplatform.org](http://code.webplatform.org).

### <span>Additional Subdomains</span>

In addition to the public-facing URL, Dabblet needs two additional subdomains for security reasons:

-   **Result preview:** This is only used internally and not displayed to the user. It's a separate domain for security reasons, otherwise people could write dabblets that leak the user's access token. On dabblet.com, this is called preview.dabblet.com
-   **Full-page results:** This is for results without any dabblet chrome around them. Separate subdomain for the same security reasons. On dabblet, this is result.dabblet.com. This is not critical, worst case we could just disable this feature.

#### <span>Why are separate subdomains needed?</span>

localStorage is local per subdomain. In dabblet, localStorage stores the user’s Github access token. An access token is a unique string Github Oauth sends to dabblet after authentication is succesfull, to identify the current user, and dabblet uses that token in subsequent requests. If executed scripts had access to dabblet’s localStorage info, they could steal the current user’s access token and send it to an arbitrary server so some attacker could use it to log in to Github as the dabblet user that access token belonged to.

### <span>Github API keys</span>

<https://github.com/organizations/webplatform/settings/applications/34604>

### <span>File edits required</span>

-   code/global.js for Client API key (Done)
-   Rename sample.oauth.php to oauth.php
-   oauth.php for domain and Client & Secret API keys (Done)
-   HTML and JS files, for the domain
-   Change .htaccess with the proper domain and subdomains (Partially done)

### <span>Git</span>

Github repo: <https://github.com/webplatform/dabblet>

TODO: Need to be able to have separate git subdirectory with the above as a remote, so we can easily pull changes. Might be a problem if we have a different structure for the subdomains (i.e. completely separate files instead of subfolders).

### <span>Deploy</span>

salt-run deploy.run code.dabblet

## <span>Branding</span>

-   Logo
-   Skinning (colors etc)
-   Prism theme (will also be used on WPD)
-   Links to WPD sections
