---
title: Things to ensure is not changed
uri: 'WPD:Infrastructure/analysis/Things to ensure is not changed'

---
## <span>Summary</span>

Infrastructure choices that should be remembered and not changed categorized by the target technology.

## <span>Softwares</span>

### <span>MediaWiki</span>

#### <span>robots.txt and the redirects</span>

Web server redirects must ensure that the <http://docs.webplatform.org/robots.txt> address **do not** redirect to <http://docs.webplatform.org/wiki/robots.txt> otherwise it changes the context and makes crawling all kinds of things that shouldn't be and might overload server capacity.