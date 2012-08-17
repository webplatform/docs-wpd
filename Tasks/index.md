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
| CJ
| 
| 
| see [[#Design|Design]]
| yes
|-
| Content Migrated
| see [[#Content_Migration|Content Migration]]
| 	
| 
| Requires MediaWiki component (some) 
| yes
|-
| Content Architecture
| see [[#Content_Architecture|Content Architecture]]
|
|
|
| yes
|-
| Original_Content
| see [[#Original_Content|Original Content]]| 	
| 
| 
|
|-
| Mobilize the MDN community to free up the content
| Mozilla
| 	
| 
| Get permissions from authors to migrate content from CC-BY-SA to CC-BY
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
| [GROUP]
| 	
| 
| Will be done by marketing team
| yes
|-
| IRC channel #webplatform
| Doug
| Done
| 
| 
| yes
|-
| Web client (IRC)
| Doug 
| Done (no skin)
| 
| Requires MediaWiki component
| 
|-
| Logging bot (IRC)
| Tech
| 	
| 
| Requires MediaWiki component
| 
|-
| Community Organization
| see [[#Community_Organization|Community Organization]]
| 
| 
| See Art of Community	
| yes
|-
| Flags
| See [[#Page_Structure| Page Structure]]
| 	
| 
| Requires MediaWiki component
| yes
|-
| Comments
| [TECH]
| 	
| 
| Requires MediaWiki component
| yes
|-
| Clear URL structure
| [GROUP]
| largely done	
| 
| 
| yes
|-
| Easy page creation
| See [[#Page_Structure| Page Structure]]
| 	
| 
| 
| 
|-
| Internationalization
| W3C I18n team
| 
| 
| We need to have a mechanism, at least a plan for it, in the beginning. Requires MediaWiki component
| yes
|-
| Language switching
| Yaron
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
| [TECH]
| 
| 
| Requires SSO, Skin. Will this hold up the launch? 
| yes
|-
| Teaching materials
| [GROUP]
| 	
| 
| Moodle? Later
| 
|-
| Federated Login feature
| [TECH]
| 
| 
| Requires MediaWiki component
| 
|-
| Required email address for accounts
| Doug
| Done	
| 
| 
| yes
|-
| Single sign in (SSO)	
| [TECH]
| 
| 
| Case by case basis
| yes
|-
| Blog
| [TECH]
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
| [GROUP] Janet
| 	
| 
| 
| yes
|-
| Privacy policy
| [GROUP], legal reps
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
| [GROUP] legal
| 	
| 
| 
| yes
|-
| Accessibility
| W3C
| 	
| 
| 
| yes
|-
| Issue tracker (bugs)
| Eliot
| 
| 
| W3C bugzilla?
| yes
|-
| Task-oriented Tutorials
| [GROUP]
| 	
| 
| 
| yes
|-
| Fast.ly CDN
| Ryan Lane	
| 
| 
| 
| yes
|-
| Copyright
| [GROUP] legal	
| 
| 
| Need to approve the terms by which people can use the content on WPD. Start with [https://www.w3.org/2011/docs/wiki/License_and_Reuse the text on the W3C Wiki].
| yes
|-
| Figure out list of "early preview" people
| [GROUP]
|
|
| Ideally include people who will actually do ''work''. Maybe give some of the people with invites a small number of invites? Have a gatekeeper of the actual signups.
| yes
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
|[GROUP]
|
|
|-
|Migrate test article from MSDN
|
|Yaron
|
|
|-
|Migrate existing articles
|
|Yaron
|
|
|-
|rowspan="3"|Figure out concrete MDN licensing flow
|New pages
|[Mozilla]
|
|
|-
|Merging content in
|[Mozilla]
|
|
|-
|SA License
|[Mozilla]
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
|[GROUP]
|
|
|-
|Create stub articles to fill out entire hierarchy
|
|[GROUP] (script?)
|
|
|-
|Language dropdown
|
|Doug/Yaron
|
|
|-
|Semantic mediawiki queries on listing/API summary pages to pull in all relevant attributes
|
|Yaron & Christian
|
|
|-
|Placement of stewards' pages
|
|Doug
|
|Webplatform.org/stewards/steward_name
|-
|Indicating standards track APIs
|
|[GROUP] 
|
|
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
|Based on Chris' [[https://www.w3.org/2011/docs/wiki/Content_requirements_master_list#Reference earlier draft of the same]].
|-
|Home page
|
|Designer. Lea? Adobe?
|
|
|-
|Section header pages
|
|[GROUP]
|
|
|-
|Marketing pages
|
|[GROUP] Millo, Christos, Ian
|
|
|-
|Create content for steward pages
|
|[GROUP]
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
|rowspan="4"|Inspect MSDN/MDN content and make sure it's compatible, and how we want this site's content to end up
| Make page mock-ups
| [GROUP]
|
| 
|-
| Make templates
| Yaron
|
| 
|-
| Make import script
| Yaron
|
| 
|-
| Verify compatibility
| Yaron
|
| 
|-
|rowspan="2" | Flags 
|Making sure we have all of the flags we need.
| Alex
|
|
|-
|Finalize flags.
| [GROUP]
|
|
|-
|rowspan="6"|Multiple articles to display end state
|Simple CSS Property
|[GROUP]
|
|
|-
|Complex CSS Property (CSS transforms)
|[GROUP]
|
|
|-
|Guide article (Canvas)
|[GROUP]
|
|
|-
|Large object: Document (lots of methods)
|[GROUP]
|
|
|-
|JS object or data type: Date
|[GROUP]
|
|
|-
|Regular Expressions
|[GROUP]
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
| Good Question
|
| 
|-
| How we maintain it
| Community
|
| 
|-
|Templates/Properties/Categories 
|
|Yaron / Kozak
|
| Created based on our content organization
|-
| Create page forms for all page types.
|
|Yaron, based on templates created by group
|
| Page forms should transclude short summaries about best practices for each section, with pop-up links to more detail.
|-
|rowspan="3" | "New page" experience 
|New page experience defined
|[GROUP]
|
| 
|-
|New page experience defined for i18n
|[GROUP]
|
| 
|-
|New page experience implemented
|Yaron / Kozak
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
|Strengthen the overall guide
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
| Alex?
|
|
|}


===Design===

{| class="wikitable"
! TOPIC
! Subtopic
! Owner
! Status
! Note
|-
| Skin
| Syntax highlighted blocks have a tag for what type of code they are
| CJ
| 
| 
|-
| Skin
| Make sure bolding looks right on Chrome
| CJ
| 
| 
|-
| Skin
| Attribution block final styling
| CJ
| 
| 
|-
| Skin
| Styling different for intra-page links, intra-wiki links, and external links
| CJ
| 
| 
|-
| Skin
| Note callouts
| CJ
| 
| 
|-
| Skin
| Section editing
| CJ
| 
| 
|-
| Skin
| Language dropdown in header
| CJ
| 
| Shows current language; allows user to select new language; also allows authenticated user to create new translation
|-
| Skin
| Username dropdown
| CJ
| 
| Needs down-arrow; item highlight; item should be whole area, not just text
|-
| Skin
| Edit / watch button colors
| CJ
| 
| Edit button should be strongest
|-
| Skin
| Search Box alignment
| CJ
| 
| Size and position should align with other visual elements 
|}