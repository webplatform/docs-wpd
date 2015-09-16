---
title: WPD:Tasks
uri: 'WPD:Tasks'

---
## Minimal Viable Product

This table tracks the tasks we want to complete before we launch webplatform.org and which ones are required to create a minimal viable product (MVP). Current categories for tasks are: Content, Marketing, and Infrastructure.

|Category|Topic|Owner|Status|Target Time (weeks)|Note|Required|
|:-------|:----|:----|:-----|:------------------|:---|:-------|
|Infra|Wiki Setup|Ryan|Done||Requires MediaWiki component|yes|
|Marketing|Skin|Marketing taskforce.|||See [Design](#Design)|yes|
|Content|Content Migrated|Content taskforce.|||See [Content Migration](#Content_Migration). Requires MediaWiki component (some)|yes|
|Content|Content Architecture|Content taskforce.|||See [Content Architecture](#Content_Architecture).|yes|
|Content|Original\_Content|Content taskforce.|||See [Original Content](#Original_Content)|||
|Content|Mobilize the MDN community to free up the content|(Janet) Mozilla|||Get permissions from authors to migrate content from CC-BY-SA to CC-BY. **Move down to content taskforce.**||
|Infra|Twitter account @webplatform|Doug|Done|||yes|
|Marketing|Twitter policy|Marketing taskforce.|||Will be done by marketing team|yes|
|Infra|IRC channel \#webplatform|Doug|Done||**Needs to be documented where it is.**|yes|
|Infra|Web client (IRC)|Doug|Done (no skin)||Requires MediaWiki component. **Needs to be documented where it is**||
|Infra|Logging bot (IRC)|Doug|||Requires MediaWiki component||
|Content|Community Organization|Content taskforce.|||See [Community Organization](#Community_Organization). See Art of Community|yes|
|Content|Flags|Content taskforce|||See [Page Structure](#Page_Structure) Requires MediaWiki component|yes|
|Infra|Comments|Doug|||Requires MediaWiki component|yes|
|Content|Clear URL structure|Content taskforce|largely done||See below.|yes|
| ???|Easy page creation|Alex|||See [Page Structure](#Page_Structure)||
|Infra|Internationalization|Doug (with support of Ryan, on behalf of W3C I18n team)|||We need to have a mechanism, at least a plan for it, in the beginning. Requires MediaWiki component|yes|
|Infra|Language switching|Ryan|||Requires MediaWiki component|yes|
|Infra|Sandbox (live viewer)|Lea|||||
|Infra|Forums (Q2A)|Doug\*|||Requires SSO, Skin. Will this hold up the launch? Needs discussion first.|yes|
|Content?|Teaching materials|Chris|||Moodle? Later||
|Infra|Federated Login feature|Doug\*|||Requires MediaWiki component||
|Infra|Required email address for accounts|Doug|Done||Doesn't work as well as necessary.|yes|
|Infra|Single sign in (SSO)|(Doug\*)|||Case by case basis. This captures that the blog and wiki need to have their login integrated.|yes|
|Infra|Blog|(Doug)|||Requires SSO, Skin. Requires MediaWiki component|yes|
|Infra|Email feedback account set up|Doug|||Others: Twitter, blog, IRC, forums, comments in topics|yes|
|Content|How to use this site|Lea & Doug||||yes|
|Content|How to help (includes migrating MDN)|Janet. (In content taskforce)||||yes|
|Content|Privacy policy|Wendy||||yes|
|Infra|Metrics and tracking|Eliot (and Doug)|||(Google analytics? Adobe? Piwik?) Create Wiki page with policy about collecting and sharing metrics.|yes|
||Metrics policy|Wendy||||yes|
|Infra|Accessibility|Chris|||This needs to be broken down into separate things. Like ensuring the site is accessible, and content on accessibility|yes|
|Infra|Issue tracker (bugs)|Eliot|Done||In W3C bugzilla. See <https://www.w3.org/Bugs/Public/describecomponents.cgi?product=webplatform.org>|yes|
|Content|Task-oriented Tutorials|Content taskforce.|||Small tutorials about how to, say, center content on the web platform.||
|Infra|Fast.ly CDN|Doug\*, Ryan Lane to do actual work.||||yes|
|Infra|System backup of site|Doug\*, Ryan Lane to do actual work.||||yes|
|Infra|Deployment script for site|Doug\*, Ryan Lane to do actual work.||||yes|
|Content|Copyright|Wendy|||Need to approve the terms by which people can use the content on WPD. Start with [the text on the W3C Wiki](https://www.w3.org/2011/docs/wiki/License_and_Reuse).|yes|
| ???|Figure out list of "early preview" people|Alex|||Ideally include people who will actually do *work*. Maybe give some of the people with invites a small number of invites? Have a gatekeeper of the actual signups.|yes|
| ???|Finalize license of web platform logo|Wendy (with Alex to help)|||||
|Marketing|Organize pre-launch hackathon|Alex (Coordinate with Eliot)|||Likely on west coast|yes|
|Marketing|Organize post-announcement community engagement (and hackathon?)|Peter (?)||||yes|

## Subtopics

These are broken out from the top-level table.

### Content Migration

<table class="wikitable">
<tr>
<th>
TOPIC

</th>
<th>
Subtopic

</th>
<th>
Owner

</th>
<th>
Status

</th>
<th>
Note

</th>
</tr>
<tr>
<td>
Figure out locations for all articles

</td>
<td>
</td>
<td>
Chris

</td>
<td>
</td>
<td>
Blocked on finalizing the URL structure. First step is to break up the list of articles to set up. Then assign people to take responsibility for each section.

</td>
</tr>
<tr>
<td>
Migrate test article from MSDN

</td>
<td>
</td>
<td>
Doug\*, work will be done by Yaron

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Migrate existing articles

</td>
<td>
</td>
<td>
Doug\*, work will be done by Yaron

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td rowspan="3">
Figure out concrete MDN licensing flow

</td>
<td>
New pages

</td>
<td>
Janet

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Merging content in

</td>
<td>
Janet

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
SA License

</td>
<td>
Janet

</td>
<td>
</td>
<td>
A manual attirbution block at bottom?

</td>
</tr>
</table>
### Content Architecture

|TOPIC|Subtopic|Owner|Status|Note|
|:----|:-------|:----|:-----|:---|
|Final URL structure/ content organization||Chris|||
|Create stub articles to fill out entire hierarchy||Chris|||
|Language dropdown||Doug\*, work done by Yaron|||
|Semantic mediawiki queries on listing/API summary pages to pull in all relevant attributes||Alex\*, work done by Yaron|||
|Placement of stewards' pages||Doug||Webplatform.org/stewards/steward\_name|
|Indicating standards track APIs||Alex||Just figuring out how to use tags/flags|

### Original Content

|TOPIC|Subtopic|Owner|Status|Note|
|:----|:-------|:----|:-----|:---|
|Comprehensive list of content needed||Chris||Based on Chris' [[earlier draft of the same](https://www.w3.org/2011/docs/wiki/Content_requirements_master_list#Reference)]. Ideally a roadmap of all the content we'll want to fill out over the years.|
|Home page||Lea|||
|Section header pages||Chris||Pages like docs/css landing page, but also sub-pages like docs/css/properties. Some of these can be somewhat auto-generated (list of sub-pages, maybe like include tutorials). Will need some templates for it.|
|Marketing pages||Wai (marketing taskforce)|||
|Create content for steward pages||*Up to each steward*|||

### Page Structure

<table class="wikitable">
<tr>
<th>
TOPIC

</th>
<th>
Subtopic

</th>
<th>
Owner

</th>
<th>
Status

</th>
<th>
Note

</th>
</tr>
<tr>
<td rowspan="5">
Inspect MSDN/MDN content and make sure it's compatible, and how we want this site's content to end up

</td>
<td>
Make page mock-ups

</td>
<td>
Doug ( with help from Lea)

</td>
<td>
</td>
<td>
Blocks on finalizing the list of all page types (next row). See the list of page types in the 6 rows below.

</td>
</tr>
<tr>
<td>
Ensure we have all page types listed on [WPD:Architecture](/WPD:Architecture)

</td>
<td>
Lea, with help from Doug

</td>
<td>
</td>
<td>
Make sure to review the whole content architecture. Make sure to include all page types, including ones that don't have templates.

</td>
</tr>
<tr>
<td>
Make templates

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Make import script

</td>
<td>
Yaron

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Figure out how to map existing content into the templates or page structure

</td>
<td>
Yaron

</td>
<td>
</td>
<td>
Chris figuring out where articles fit, Alex figuring out how the content fits in, and Yaron implementing

</td>
</tr>
<tr>
<td rowspan="3">
Flags

</td>
<td>
Making sure we have all of the flags we need.

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Finalize flags.

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Implement flags that can take a string value as well (e.g. merge candidate)

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td rowspan="6">
Multiple articles to display end state

</td>
<td>
Simple CSS Property

</td>
<td>
N/A

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Complex CSS Property (CSS transforms)

</td>
<td>
N/A

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Guide article (Canvas)

</td>
<td>
N/A

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Large object: Document (lots of methods)

</td>
<td>
N/A

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
JS object or data type: Date

</td>
<td>
N/A

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Regular Expressions

</td>
<td>
N/A

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td rowspan="3">
Figure out compatibility table design

</td>
<td>
How it looks

</td>
<td>
CJ

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
How it gets populated

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
How we maintain it

</td>
<td>
Alex

</td>
<td>
</td>
<td>
Just in the best practices / style guide. In the long run may want to have it automated.

</td>
</tr>
<tr>
<td>
Templates/Properties/Categories

</td>
<td>
</td>
<td>
Alex

</td>
<td>
</td>
<td>
Created based on our content organization

</td>
</tr>
<tr>
<td>
Create page forms for all page types.

</td>
<td>
</td>
<td>
Alex

</td>
<td>
</td>
<td>
Page forms should transclude short summaries about best practices for each section, with pop-up links to more detail.

</td>
</tr>
<tr>
<td rowspan="3">
"New page" experience

</td>
<td>
New page experience defined

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
New page experience defined for i18n

</td>
<td>
Doug

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
New page experience implemented

</td>
<td>
Alex

</td>
<td>
</td>
<td>
</td>
</tr>
</table>
### Community Organization

|TOPIC|Subtopic|Owner|Status|Note|
|:----|:-------|:----|:-----|:---|
|Tighten up pillars doc||Alex|||
|Strengthen the overall guide (practical counterpart to pillars)||Alex, b/c he knows what this one means.|||
|Beef up "Getting Started" guide||Doug / Lea|||
|Create style guide for code examples||Eliot|In progress||
|Finalize the Manual of Style (including sub pages)||Alex|||
|Figure out about badges and community recognition||Peter Lubbers|||

### Design

**Handled by the marketing taskforce**

<table class="wikitable">
<tr>
<th>
TOPIC

</th>
<th>
Subtopic

</th>
<th>
Owner

</th>
<th>
Status

</th>
<th>
Note

</th>
</tr>
<tr>
<td rowspan="12">
Design

</td>
<td>
Attribution block final styling

</td>
<td>
CJ

</td>
<td>
[Open](http://webplatform.org/docs/File:attribution1.png%20)[Closed](http://webplatform.org/docs/File:attribution2.png%20)

</td>
<td>
</td>
</tr>
<tr>
<td>
Links

</td>
<td>
CJ

</td>
<td>
</td>
<td>
Styling different for intra-page links, intra-wiki links, external links, and links to non-existing pages

</td>
</tr>
<tr>
<td>
Note callouts

</td>
<td>
CJ

</td>
<td>
[Example](http://webplatform.org/docs/File:notes.png%20)

</td>
<td>
</td>
</tr>
<tr>
<td>
Language dropdown in header

</td>
<td>
CJ

</td>
<td>
[Open](http://webplatform.org/docs/File:language2.png%20)[Closed](http://webplatform.org/docs/File:language.png%20)

</td>
<td>
Shows current language; allows user to select new language; also allows authenticated user to create new translation

</td>
</tr>
<tr>
<td>
Search Box alignment

</td>
<td>
CJ

</td>
<td>
Done

</td>
<td>
Size and position should align with other visual elements

</td>
</tr>
<tr>
<td>
[CSS Prefix](/Template:CSS_Prefix) callouts need to be styled

</td>
<td>
CJ

</td>
<td>
[Example](http://webplatform.org/docs/File:prefix.png%20)

</td>
<td>
</td>
</tr>
<tr>
<td>
Design style guide

</td>
<td>
CJ

</td>
<td>
[File:Web-Platform-Style-Guide-web-1.pdf](/File:Web-Platform-Style-Guide-web-1.pdf)

</td>
<td>
Provides guidlines for creating sub-properties like blog, IRC, etc.

</td>
</tr>
<tr>
<td>
Compatibility table styling

</td>
<td>
CJ

</td>
<td>
[Example](http://webplatform.org/docs/File:prefix.png%20)

</td>
<td>
For an example, see [css/properties/font-size](/css/properties/font-size)

</td>
</tr>
<tr>
<td>
Stewards Page Design

</td>
<td>
CJ

</td>
<td>
[Example](http://webplatform.org/docs/File:Stewards_Page.png%20)

</td>
<td>
Extensible to work for each steward, unique page for each

</td>
</tr>
<tr>
<td>
Landing Page Design

</td>
<td>
CJ

</td>
<td>
[Examples](/WPD:Design/Landing)

</td>
<td>
</td>
</tr>
<tr>
<td>
Static Page Design

</td>
<td>
CJ

</td>
<td>
[Blog Example](http://webplatform.org/docs/File:Static_Page_Blog.png%20)

[Q/A Example](http://webplatform.org/docs/File:Static_Page_QA.png%20)

</td>
<td>
</td>
</tr>
<tr>
<td>
Styling for language tags in examples

</td>
<td>
CJ

</td>
<td>
[Example](http://webplatform.org/docs/File:code_language.png%20)

</td>
<td>
See [css/properties/font-size](/css/properties/font-size) for an example.

</td>
</tr>
<tr>
<td>
Footer

</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Community Badges

</td>
<td>
</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td rowspan="8">
Skin

</td>
<td>
External attribution blocks use something equivalent to details/summary elements

</td>
<td>
Doug\*

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Make sure bolding looks right on Chrome

</td>
<td>
Doug\*

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Section editing

</td>
<td>
Doug\*

</td>
<td>
</td>
<td>
</td>
</tr>
<tr>
<td>
Username dropdown

</td>
<td>
Doug\*

</td>
<td>
</td>
<td>
Needs down-arrow; item highlight; item should be whole area, not just text

</td>
</tr>
<tr>
<td>
[Editorial](/Template:Editorial) callouts should only show for logged-in users (via CSS)

</td>
<td>
Doug\*

</td>
<td>
</td>
<td>
This should probably be as simple as having a `.editors-only { display:none}` rule in the CSS file, so we can create new templates that are hidden from readers easily.

</td>
</tr>
<tr>
<td>
Edit / watch button colors

</td>
<td>
Doug\*

</td>
<td>
</td>
<td>
Edit button should be strongest

</td>
</tr>
<tr>
<td>
Syntax highlighting of examples with prism.js

</td>
<td>
Lea

</td>
<td>
</td>
<td>
Will need to modify [Template:Single\_Example](/Template:Single_Example)

</td>
</tr>
<tr>
<td>
Style the standardization flag.

</td>
<td>
Doug

</td>
<td>
</td>
<td>
[Template:Standardization\_Status](/Template:Standardization_Status)

</td>
</tr>
</table>
