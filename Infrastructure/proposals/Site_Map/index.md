---
title: 'Site Map'
uri: 'WPD:Infrastructure/proposals/Site Map'

---
**Note**: This page describes the initial plan for webplatform.org, most content is deprecated

## Landing Page

WebPlatform.org

**uri:** webplatform.org

### Content

-   Project description
-   Partners
-   Get Involved
-   News (?)
-   Blog: summaries of current developments in open web platform
    -   [WordPress](http://wordpress.org/)

### Sub-Pages

-   Web standards
    -   Standards Development Organizations (SDOs): W3C, IETF, Khronos, WHATWG, etc.
    -   Getting involved in standards: email discussions, use cases and requirements, tests, demos, filing bugs, documentation
-   Profile pages for contributors and organizations
-    ?

## Docs

**uri:** webplatform.org/docs/

### Content

-   Reference docs
-   Guides
-   Tutorials

### Software

-   [MediaWiki](http://www.mediawiki.org/wiki/MediaWiki) with extensions:

|Extension|Installed|Deployed|git|Comments|
|:--------|:--------|:-------|:--|:-------|
|Semantic MediaWiki|✓|✓|✓||
|Semantic Forms|✓|✓|✓||
|[Admin\_Links](http://www.mediawiki.org/wiki/Extension:Admin_Links)|✓|✓|✓||
|[ArticleFeedback](http://www.mediawiki.org/wiki/Extension:ArticleFeedback)|✓|✓|✓||
|[ConfirmAccount](http://www.mediawiki.org/wiki/Extension:ConfirmAccount)|✓| ?||Installed, but not clear it's working|
|[ConfirmEdit](http://www.mediawiki.org/wiki/Extension:ConfirmEdit)|✓||✓|Provides CAPTCHA options.|
|[ApprovedRevs](http://www.mediawiki.org/wiki/Extension:Approved_Revs)|✓||✓|For curation and approval of edits, on per-page basis. A more complicated option is [FlaggedRevs](http://www.mediawiki.org/wiki/Extension:FlaggedRevs).|
|[SyntaxHighlight\_GeSHi](http://www.mediawiki.org/wiki/Extension:SyntaxHighlight_GeSHi)|✓|✓|✓|Syntax highlighting. (Allow each line to be linked to: [\$geshi-\>enable\_ids(true);](http://qbnz.com/highlighter/geshi-doc.html#adding-ids-to-each-line))|
|[SocialProfile](http://www.mediawiki.org/wiki/Extension:SocialProfile)|||||
|[Ajax Poll](http://www.mediawiki.org/wiki/Extension:AJAX_Poll)|||||
|[AjaxLogin](http://www.mediawiki.org/wiki/Extension:AjaxLogin)|||||
|[ApiExplorer](http://www.mediawiki.org/wiki/Extension:ApiExplorer)|||||
|[EditSimilar](http://www.mediawiki.org/wiki/Extension:EditSimilar)|||||
|[LinkSuggest](http://www.mediawiki.org/wiki/Extension:LinkSuggest)|||||
|[WhosOnline](http://www.mediawiki.org/wiki/Extension:WhosOnline)|||||
|[Video](http://www.mediawiki.org/wiki/Extension:Video)|||||
|[HAWelcome](http://www.mediawiki.org/wiki/Extension:HAWelcome)||||Automatically welcomes users on their first edit.|
|[SuggestBot](http://en.wikipedia.org/wiki/User:SuggestBot)||||A Mediawiki bot that suggests pages to users to edit, based on their past edits.|
|[PCR GUI Inserts](http://www.mediawiki.org/wiki/Extension:PCR_GUI_Inserts#Adding_a_Piwik_statistics_code_at_the_bottom)||||Site traffic analytics, requires [Piwik](http://piwik.org/) to be installed on server|
|[WikiFactory](http://www.mediawiki.org/wiki/Extension:WikiFactory)||||Admin interface for enabling extensions, etc.|
|[SphinxSearch](http://www.mediawiki.org/wiki/Extension:SphinxSearch)|||✓|Improved site search, requires [Sphinx Search Engine](http://sphinxsearch.com/downloads/) to be installed on server|

## Teaching Material

**uri:** webplatform.org/teach/

### Content

-   Curricula
-   Lesson plans
-   Sample test questions
-   Teaching guides
-   Forums

### Software

-   [Moodle](http://moodle.org/): a tool many teacher already use

## Discussion / Help Forums

**uri:** webplatform.org/talk/

### Content

-   Web-based IRC client tied to dedicated \#webplatform IRC channel
-   Forums

### Software

-   [qwebirc](http://www.qwebirc.org/): a web-based IRC client
    -   see [borknet](http://www.borknet.org/index.php?topic=irc&page=qwebirc) for an example of a well-integrated web-based IRC client and [freenode webchat](http://webchat.freenode.net/) for an example with a captcha
-   logging bot, like [IrcLogger](http://colas.nahaboo.net/Software/IrcLogger) or [wm-bot](http://bots.wmflabs.org/~wm-bot/)
    -   include HTML logs, with highlighting and linking, like [Krijn Hoetmer's logs](http://krijnhoetmer.nl/irc-logs/whatwg/20120604)
-   [Question2Answer](http://www.question2answer.org/): Q/A Forums (a la StackOverflow)

## User Profiles

**uri:** webplatform.org/profiles/

### Content

-   User bios
-   Contribution lists (by user)
-   Organization and "Team" pages
    -   Linked lists of users

## Tools

*Lower priority; Phase 2*

**uri:** webplatform.org/tools/

### Content

?

### Software

-   pastebin
-   live code tester
    -   [Dabblet](http://dabblet.com/)
-   live DOM viewer
-   validation
