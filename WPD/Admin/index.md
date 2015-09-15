---
title: WPD:Admin
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - 'WPD:Admin/Autoconfirm'
uri: 'WPD:Admin'

---
There are several special pages that Stewards should know about:

-   [The Article Feedback dashboard](/Special:ArticleFeedback), listing pages with highest and lowest ratings, as well as recent lows
-   [Special:AdminLinks](/Special:AdminLinks), which functions like a dashboard, with helpful links. This is handy for create templates.
-   [The Mediawiki version page](/Special:Version), including all information about our current installation, such as extensions
-   [Mediawiki Deployment Instructions](/Meta:Deployment), for installing extensions, adding software to the site, etc.
-   [Site Map](/WPD:Site_Map), including site architecture and software requirements
-   **?uselang=qqx** appended to any page give you special information about that page

## <span>Site Metrics</span>

-   [Site Metrics](/WPD:Admin/Site_Metrics)
-   [Special:Statistics](/Special:Statistics)
-   [WikiMedia discussion on a useful community portal for Wikipedia editors](https://meta.wikimedia.org/wiki/Research:Community_portal_redesign)

## <span>Account Creation</span>

Currently, only registered account holders can view pages on the wiki.

-   [UserLogin](/Special:UserLogin) allows *bureaucrats* to create accounts
-   [Request Account](/Special:RequestAccount) allows users to ask for an account
-   [Confirm Accounts](/Special:ConfirmAccounts) allows *bureaucrats* to approve requested accounts
-   [Autoconfirm](/w/index.php?title=WPD:Admin/Autoconfirm&action=edit&redlink=1) allows Admins to override spam controls for known users

## <span>Content Management</span>

-   [Special:ReplaceText](/Special:ReplaceText) allows admins to search and replace across multiple pages on the wiki using regular expressions. See [usage instructions](http://www.mediawiki.org/wiki/Extension:Replace_Text#Usage) for more details.
-   [Nuke](/Special:Nuke) allows admins to mass delete all edits by a particular user, IP address, etc.
    -   [Log/delete](/Special:Log/delete) shows all pages which have been deleted

## <span>Miscellaneous</span>

### <span>Debugging</span>

You can bypass fastly completely by curling directly to an app server and passing the host header; so rather than just seeing a 500, you can see an actual exception:

    curl 'http://15.185.108.248/w/api.php' -H 'Host: docs.webplatform.org'