==Minimal Viable Product==
This table tracks the tasks we want to complete before we launch webplatform.org and which ones are required to create a minimal viable product (MVP).  Current categories for tasks are: Content, Marketing, and Infrastructure.

{| class="wikitable sortable"
! Category
! Topic
! Owner
! Status
! Target Time (weeks)
! Note
! Required 
|-
| Infra
| Wiki Setup
| Ryan
| Done                                         
| 
| Requires MediaWiki component
| yes
|-
| Marketing
| Skin
| Marketing taskforce. 
| 
| 
| See [[#Design|Design]]
| yes
|-
| Content
| Content Migrated
| Content taskforce. 
| 	
| 
| See [[#Content_Migration|Content Migration]]. Requires MediaWiki component (some) 
| yes
|-
| Content
| Content Architecture
| Content taskforce. 
|
|
| See [[#Content_Architecture|Content Architecture]].
| yes
|-
| Content
| Original_Content
| Content taskforce. 
| 
|
| See [[#Original_Content|Original Content]]| 	 
|
|-
| Content
| Mobilize the MDN community to free up the content
| (Janet) Mozilla
| 	
| 
| Get permissions from authors to migrate content from CC-BY-SA to CC-BY. '''Move down to content taskforce.'''
|
|-
| Infra
| Twitter account @webplatform
| Doug
| Done	
| 
| 
| yes
|-
| Marketing
| Twitter policy 
| Marketing taskforce.
| 	
| 
| Will be done by marketing team
| yes
|-
| Infra
| IRC channel #webplatform
| Doug
| Done
| 
| '''Needs to be documented where it is.'''
| yes
|-
| Infra
| Web client (IRC)
| Doug 
| Done (no skin)
| 
| Requires MediaWiki component. '''Needs to be documented where it is'''
| 
|-
| Infra
| Logging bot (IRC)
| Doug
| 	
| 
| Requires MediaWiki component
| 
|-
| Content
| Community Organization
| Content taskforce. 
| 
| 
| See [[#Community_Organization|Community Organization]]. See Art of Community	
| yes
|-
| Content
| Flags
| Content taskforce
| 	
| 
| See [[#Page_Structure| Page Structure]] Requires MediaWiki component
| yes
|-
| Infra
| Comments
| Doug
| 	
| 
| Requires MediaWiki component
| yes
|-
| Content
| Clear URL structure
| Content taskforce
| largely done	
| 
| See below.
| yes
|-
| ???
| Easy page creation
| Alex
| 	
| 
| See [[#Page_Structure| Page Structure]]
| 
|-
| Infra
| Internationalization
| Doug (with support of Ryan, on behalf of W3C I18n team)
| 
| 
| We need to have a mechanism, at least a plan for it, in the beginning. Requires MediaWiki component
| yes
|-
| Infra
| Language switching
| Ryan
| 
| 
| Requires MediaWiki component
| yes
|-
| Infra
| Sandbox (live viewer)
| Lea
| 	
| 
| 
| 
|-
| Infra
| Forums (Q2A)
| Doug*
| 
| 
| Requires SSO, Skin. Will this hold up the launch?  Needs discussion first.
| yes
|-
| Content?
| Teaching materials
| Chris
| 	
| 
| Moodle? Later
| 
|-
| Infra
| Federated Login feature
| Doug*
| 
| 
| Requires MediaWiki component
| 
|-
| Infra
| Required email address for accounts
| Doug
| Done	
| 
| Doesn't work as well as necessary.
| yes
|-
| Infra
| Single sign in (SSO)	
| (Doug*)
| 
| 
| Case by case basis. This captures that the blog and wiki need to have their login integrated.
| yes
|-
| Infra
| Blog
| (Doug)
| 
| 
| Requires SSO, Skin. Requires MediaWiki component
| yes
|-
| Infra
| Email feedback account set up
| Doug
|
| 
| Others: Twitter, blog, IRC, forums, comments in topics
| yes
|-
| Content
| How to use this site
| Lea & Doug
| 
| 
| 	
| yes
|-
| Content
| How to help (includes migrating MDN)
| Janet. (In content taskforce)
| 	
| 
| 
| yes
|-
| Content
| Privacy policy
| Wendy
| 	
| 
| 
| yes
|-
| Infra
| Metrics and tracking 
| Eliot (and Doug)
| 	
| 
| (Google analytics? Adobe? Piwik?) Create Wiki page with policy about collecting and sharing metrics.
| yes
|-
| 
| Metrics policy
| Wendy
| 	
| 
| 
| yes
|-
| Infra
| Accessibility
| Chris
| 	
| 
| This needs to be broken down into separate things. Like ensuring the site is accessible, and content on accessibility
| yes
|-
| Infra
| Issue tracker (bugs)
| Eliot
| Done
| 
| In W3C bugzilla. See [https://www.w3.org/Bugs/Public/describecomponents.cgi?product=webplatform.org https://www.w3.org/Bugs/Public/describecomponents.cgi?product=webplatform.org]
| yes
|-
| Content
| Task-oriented Tutorials
| Content taskforce.
| 	
| 
| Small tutorials about how to, say, center content on the web platform.
| 
|-
| Infra
| Fast.ly CDN
| Doug*, Ryan Lane to do actual work.
| 
| 
| 
| yes
|-
| Infra
| System backup of site
| Doug*, Ryan Lane to do actual work.
| 
| 
| 
| yes
|-
| Infra
| Deployment script for site
| Doug*, Ryan Lane to do actual work.
| 
| 
| 
| yes
|-
| Content
| Copyright
| Wendy
| 
| 
| Need to approve the terms by which people can use the content on WPD. Start with [https://www.w3.org/2011/docs/wiki/License_and_Reuse the text on the W3C Wiki].
| yes
|-
| ???
| Figure out list of "early preview" people
| Alex
|
|
| Ideally include people who will actually do ''work''. Maybe give some of the people with invites a small number of invites? Have a gatekeeper of the actual signups.
| yes
|-
| ???
| Finalize license of web platform logo
| Wendy (with Alex to help)
|
|
| 
|
|-
| Marketing
| Organize pre-launch hackathon
| Alex (Coordinate with Eliot)
|
|
| Likely on west coast
|  yes
|-
| Marketing
| Organize post-announcement community engagement (and hackathon?)
| Peter (?)
|
|
| 
|  yes
|}

==Subtopics==

These are broken out from the top-level table.




===Content Migration===
{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
|Figure out locations for all articles
|
| Chris
|
| Blocked on finalizing the URL structure. First step is to break up the list of articles to set up. Then assign people to take responsibility for each section.
|-
| Migrate test article from MSDN
|
| Doug*, work will be done by Yaron 
|
| 
|-
|Migrate existing articles
|
| Doug*, work will be done by Yaron
|
|
|-
|rowspan="3"|Figure out concrete MDN licensing flow
|New pages
| Janet
|
|
|-
|Merging content in
| Janet
|
|
|-
|SA License
| Janet
|
|A manual attirbution block at bottom?
|}

===Content Architecture===
{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
|Final URL structure/ content organization
|
| Chris
|
|
|-
|Create stub articles to fill out entire hierarchy
|
| Chris
|
|
|-
|Language dropdown
|
| Doug*, work done by Yaron
|
|
|-
|Semantic mediawiki queries on listing/API summary pages to pull in all relevant attributes
|
| Alex*, work done by Yaron
|
|
|-
|Placement of stewards' pages
|
| Doug
|
|Webplatform.org/stewards/steward_name
|-
|Indicating standards track APIs
|
| Alex
|
| Just figuring out how to use tags/flags
|}

===Original Content===
{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
|Comprehensive list of content needed
|
|Chris
|
|Based on Chris' [[https://www.w3.org/2011/docs/wiki/Content_requirements_master_list#Reference earlier draft of the same]]. Ideally a roadmap of all the content we'll want to fill out over the years.
|-
|Home page
|
| Lea
|
|
|-
|Section header pages
|
| Chris
|
| Pages like docs/css landing page, but also sub-pages like docs/css/properties. Some of these can be somewhat auto-generated (list of sub-pages, maybe like include tutorials). Will need some templates for it.
|-
|Marketing pages
|
| Wai (marketing taskforce)
|
|
|-
|Create content for steward pages
|
| ''Up to each steward''
|
|
|}

===Page Structure===
{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
|rowspan="5"|Inspect MSDN/MDN content and make sure it's compatible, and how we want this site's content to end up
| Make page mock-ups
| Doug ( with help from Lea)
| 
| Blocks on finalizing the list of all page types (next row). See the list of page types in the 6 rows below.
|- 
| Ensure we have all page types listed on [[WPD:Architecture]]
| Lea, with help from Doug
| 
| Make sure to review the whole content architecture. Make sure to include all page types, including ones that don't have templates.
|-
| Make templates
| Alex
|
| 
|-
| Make import script
| Yaron
|
| 
|-
| Figure out how to map existing content into the templates or page structure
| Yaron
|
| Chris figuring out where articles fit, Alex figuring out how the content fits in, and Yaron implementing
|-
|rowspan="3" | Flags 
|Making sure we have all of the flags we need.
| Alex
|
|
|-
|Finalize flags.
| Alex
|
|
|-
| Implement flags that can take a string value as well (e.g. merge candidate)
| Alex
|
|
|-
|rowspan="6"|Multiple articles to display end state
|Simple CSS Property
| N/A
|
|
|-
|Complex CSS Property (CSS transforms)
| N/A
|
|
|-
|Guide article (Canvas)
| N/A
|
|
|-
|Large object: Document (lots of methods)
|N/A
|
|
|-
|JS object or data type: Date
|N/A
|
|
|-
|Regular Expressions
|N/A
|
|
|-
|rowspan="3"|Figure out compatibility table design
| How it looks
| CJ 
|
| 
|-
| How it gets populated
| Alex
|
| 
|-
| How we maintain it
| Alex
|
| Just in the best practices / style guide. In the long run may want to have it automated.
|-
|Templates/Properties/Categories 
|
| Alex
|
| Created based on our content organization
|-
| Create page forms for all page types.
|
| Alex
|
| Page forms should transclude short summaries about best practices for each section, with pop-up links to more detail.
|-
|rowspan="3" | "New page" experience 
|New page experience defined
| Alex
|
| 
|-
|New page experience defined for i18n
|  Doug
|
| 
|-
|New page experience implemented
| Alex
|
| 
|}

===Community Organization===

{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
|Tighten up pillars doc
|
|Alex
|
|
|-
|Strengthen the overall guide (practical counterpart to pillars)
|
|Alex, b/c he knows what this one means.
|
|
|-
|Beef up "Getting Started" guide
|
|Doug / Lea
|
|
|-
|Create style guide for code examples
|
|Eliot
|In progress
|
|-
| Finalize the Manual of Style (including sub pages)
|
| Alex
|
|
|-
| Figure out about badges and community recognition
|
| Peter Lubbers
|
|
|}

===Design===
'''Handled by the marketing taskforce'''
{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
|rowspan="12"| Design
| Attribution block final styling
| CJ
| [[File:attribution1.png|Example closed]][[File:attribution2.png|Example open]]
| 
|-
| Links
| CJ
| 
| Styling different for intra-page links, intra-wiki links, external links, and links to non-existing pages
|-
| Note callouts
| CJ
| 
| 
|-
| Language dropdown in header
| CJ
| 
| Shows current language; allows user to select new language; also allows authenticated user to create new translation
|-
| Search Box alignment
| CJ
| Done
| Size and position should align with other visual elements 
|-
| [[Template:CSS_Prefix | CSS Prefix]] callouts need to be styled
| CJ
|
|
|-
| Design style guide
| CJ
|
| Provides guidlines for creating sub-properties like blog, IRC, etc.
|-
| Compatibility table styling
| CJ
|
| For an example, see [[css/properties/font-size]]
|-
| Stewards Page Design
| CJ
| 
| Extensible to work for each steward, unique page for each
|-
| Landing Page Design
| CJ
| 
| 
|-
| Static Page Design
| CJ
| 
|
|-
| Styling for language tags in examples
| CJ
| 
| See [[css/properties/font-size]] for an example.
|-
|rowspan="7"| Skin
| External attribution blocks use something equivalent to details/summary elements
| Doug*
| 
| 
|-
| Make sure bolding looks right on Chrome
| Doug*
| 
| 
|-
| Section editing
| Doug*
| 
| 
|-
| Username dropdown
| Doug*
| 
| Needs down-arrow; item highlight; item should be whole area, not just text
|-
| [[Template:Editorial | Editorial]] callouts should only show for logged-in users (via CSS)
| Doug*
| 
| This should probably be as simple as having a <code>.editors-only { display:none}</code> rule in the CSS file, so we can create new templates that are hidden from readers easily.
|-
| Edit / watch button colors
| Doug*
| 
| Edit button should be strongest
|-
| Syntax highlighting of examples with prism.js
| Lea
| 
| Will need to modify [[Template:Single_Example]]
|}