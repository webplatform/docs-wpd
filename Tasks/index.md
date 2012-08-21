==Minimal Viable Product==
This table tracks the tasks we want to complete before we launch webplatform.org and which ones are required to create a minimal viable product (MVP) 

{| class="wikitable sortable"
! Topic
! Owner
! Status
! Target Time (weeks)
! Note
! Required 
|-
| Wiki Setup
| Ryan
| Done                                         
| 
| Requires MediaWiki component
| yes
|-
| Skin
| Marketing taskforce. 
| 
| 
| See [[#Design|Design]]
| yes
|-
| Content Migrated
| Content taskforce. 
| 	
| 
| See [[#Content_Migration|Content Migration]]. Requires MediaWiki component (some) 
| yes
|-
| Content Architecture
| Content taskforce. 
|
|
| See [[#Content_Architecture|Content Architecture]].
| yes
|-
| Original_Content
| Content taskforce. 
| 
|
| See [[#Original_Content|Original Content]]| 	 
|
|-
| Mobilize the MDN community to free up the content
| (Janet) Mozilla
| 	
| 
| Get permissions from authors to migrate content from CC-BY-SA to CC-BY. '''Move down to content taskforce.'''
|
|-
| Twitter account @webplatform
| Doug
| Done	
| 
| 
| yes
|-
| Twitter policy 
| Marketing taskforce.
| 	
| 
| Will be done by marketing team
| yes
|-
| IRC channel #webplatform
| Doug
| Done
| 
| '''Needs to be documented where it is.'''
| yes
|-
| Web client (IRC)
| Doug 
| Done (no skin)
| 
| Requires MediaWiki component. '''Needs to be documented where it is'''
| 
|-
| Logging bot (IRC)
| Doug
| 	
| 
| Requires MediaWiki component
| 
|-
| Community Organization
| Content taskforce. 
| 
| 
| See [[#Community_Organization|Community Organization]]. See Art of Community	
| yes
|-
| Flags
| Content taskforce
| 	
| 
| See [[#Page_Structure| Page Structure]] Requires MediaWiki component
| yes
|-
| Comments
| Doug
| 	
| 
| Requires MediaWiki component
| yes
|-
| Clear URL structure
| Content taskforce
| largely done	
| 
| See below.
| yes
|-
| Easy page creation
| Alex
| 	
| 
| See [[#Page_Structure| Page Structure]]
| 
|-
| Internationalization
| Doug (with support of Ryan, on behalf of W3C I18n team)
| 
| 
| We need to have a mechanism, at least a plan for it, in the beginning. Requires MediaWiki component
| yes
|-
| Language switching
| Ryan
| 
| 
| Requires MediaWiki component
| yes
|-
| Sandbox (live viewer)
| Lea
| 	
| 
| 
| 
|-
| Forums (Q2A)
| Doug*
| 
| 
| Requires SSO, Skin. Will this hold up the launch?  Needs discussion first.
| yes
|-
| Teaching materials
| Chris
| 	
| 
| Moodle? Later
| 
|-
| Federated Login feature
| Doug*
| 
| 
| Requires MediaWiki component
| 
|-
| Required email address for accounts
| (Doug)
| Pending	
| 
| Doesn't work as well as necessary.
| yes
|-
| Single sign in (SSO)	
| (Doug*)
| 
| 
| Case by case basis. This captures that the blog and wiki need to have their login integrated.
| yes
|-
| Blog
| (Doug)
| 
| 
| Requires SSO, Skin. Requires MediaWiki component
| yes
|-
| Email feedback account set up
| Doug
|
| 
| Others: Twitter, blog, IRC, forums, comments in topics
| yes
|-
| How to use this site
| Lea & Doug
| 
| 
| 	
| yes
|-
| How to help (includes migrating MDN)
| Janet. (In content taskforce)
| 	
| 
| 
| yes
|-
| Privacy policy
| Wendy
| 	
| 
| 
| yes
|-
| Metrics and tracking 
| Eliot
| 	
| 
| (Google analytics? Adobe?) Create Wiki page.
| yes
|-
| Metrics policy
| Wendy
| 	
| 
| 
| yes
|-
| Accessibility
| Chris
| 	
| 
| This needs to be broken down into separate things. Like ensuring the site is accessible, and content on accessibility
| yes
|-
| Issue tracker (bugs)
| Eliot
| Done
| 
| In W3C bugzilla. See [https://www.w3.org/Bugs/Public/describecomponents.cgi?product=webplatform.org https://www.w3.org/Bugs/Public/describecomponents.cgi?product=webplatform.org]
| yes
|-
| Task-oriented Tutorials
| Content taskforce.
| 	
| 
| Small tutorials about how to, say, center content on the web platform.
| 
|-
| Fast.ly CDN
| Doug*, Ryan Lane to do actual work.
| 
| 
| 
| yes
|-
| System backup of site
| Doug*, Ryan Lane to do actual work.
| 
| 
| 
| yes
|-
| Deployment script for site
| Doug*, Ryan Lane to do actual work.
| 
| 
| 
| yes
|-
| Copyright
| Wendy
| 
| 
| Need to approve the terms by which people can use the content on WPD. Start with [https://www.w3.org/2011/docs/wiki/License_and_Reuse the text on the W3C Wiki].
| yes
|-
| Figure out list of "early preview" people
| Alex
|
|
| Ideally include people who will actually do ''work''. Maybe give some of the people with invites a small number of invites? Have a gatekeeper of the actual signups.
| yes
|-
| Finalize license of web platform logo
| Wendy (with Alex to help)
|
|
| 
|
|-
| Organize pre-launch hackathon
| Alex (Coordinate with Eliot)
|
|
| Likely on west coast
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
|
|
|-
| Finalize the Manual of Style (including sub pages)
|
| Alex
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
|rowspan="8"| Design
| Attribution block final styling
| CJ
| 
| 
|-
| Styling different for intra-page links, intra-wiki links, and external links
| CJ
| 
| 
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
| I believe this is done, I have the search box/buttons/TOC right aligned with each other and the search input copy the same font size as the rest of the header copy.  Let me know if there are any other desired changes.
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
|rowspan="6"| Skin
| Syntax highlighted blocks have a tag for what type of code they are
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
| 
|-
| Edit / watch button colors
| Doug*
| 
| Edit button should be strongest
|}