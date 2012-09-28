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




{| class="sortable wikitable"|
! Topic
! URL
! How to generate content? 
! Priority Status
! Notes
|-
| All Topics
| /  
| Manual 
| P0
| Not Started 
|-
|rowspan="11"| Concepts  
| /concepts  
| Sub-Directory
| P0
| Not Started 
|-
| /concepts/accessibility
| Query 
| P1
| Not Started 
|-
| /concepts/IA
| Query 
| P1
| Not Started 
|-
| /concepts/internet_and_web
| Query 
| P1
| Not Started 
|-
| /concepts/one_web
| Query 
| P1
| Not Started 
|-
| /concepts/progressive_enhancement
| Query 
| P1
| Not Started 
|-
| /concepts/security
| Query 
| P1
| Not Started 
|-
| /concepts/usability
| Query 
| P1
| Not Started 
|-
| /concepts/user_profiling
| Query 
| P1
| Not Started 
|-
| /concepts/UX
| Query 
| P1
| Not Started 
|-
| /concepts/mobile_web 
| Sub-Directory
| P1
| Not Started For mobile section Batch 14
|-
|rowspan="10"| HTML
| /html
| Sub-Directory
| P0
| Not Started 
|-
| /html/validation
| Query
| P2
| Not Started 
|-
| /html/quirks_mode
| Query
| P2
| Not Started 
|-
| /html/data_types
| Query
| P2
| Not Started 
|-
| /html/elements
| Sub-Directory
| P0
| Not Started 
|-
| /html/attributes 
| Sub-Directory
| P0
| Not Started 
|-
| /html/apis
| Query
| P3
| Not Started 
|-
| /html/apis/methods
| Query
| P3
| Not Started 
|-
| /html/apis/properties
| Query
| P3
| Not Started 
|-
| /html/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="14"| CSS 
| /css 
| Sub-Directory
| P0
| Not Started 
|-
| /css/inheritance
| Query
| P2
| Not Started 
|-
| /css/cascade
| Query
| P2
| Not Started 
|-
| /css/vendor_prefixes
| Query
| P2
| Not Started 
|-
| /css/data_types  
| Sub-Directory
| P1
| Not Started 
|-
| /css/properties  
| Sub-Directory
| P1
| Not Started 
|-
| /css/functions
| Sub-Directory
| P1
| Not Started 
|-
| /css/keywords 
| Sub-Directory
| P1
| Not Started 
|-
| /css/selectors
| Sub-Directory
| P1
| Not Started 
|-
| /css/atrules  
| Sub-Directory
| P1
| Not Started 
|-
| /css/apis
| Query
| P3
| Not Started 
|-
| /css/apis/methods
| Query
| P3
| Not Started 
|-
| /css/apis/properties
| Query
| P3
| Not Started 
|-
| /css/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="8"| SVG
| /svg 
| Sub-Directory
| P0
| Not Started 
|-
| /svg/data_types  
| Sub-Directory
| P1
| Not Started 
|-
| /svg/elements 
| Sub-Directory
| P1
| Not Started 
|-
| /svg/attributes  
| Sub-Directory
| P1
| Not Started 
|-
| /svg/apis
| Query
| P3
| Not Started 
|-
| /svg/apis/properties
| Query
| P3
| Not Started 
|-
| /svg/apis/methods
| Query
| P3
| Not Started 
|-
| /svg/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="5"| Canvas
| /canvas 
| Sub-Directory
| P0
| Not Started 
|-
| /canvas/apis
| Query
| P3
| Not Started 
|-
| /canvas/apis/properties
| Query
| P3
| Not Started 
|-
| /canvas/apis/methods
| Query
| P3
| Not Started 
|-
| /canvas/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="5"| WebGL
| /webgl 
| Sub-Directory
| P0
| Not Started 
|-
| /webgl/apis
| Query
| P3
| Not Started 
|-
| /webgl/apis/properties
| Query
| P3
| Not Started 
|-
| /webgl/apis/methods
| Query
| P3
| Not Started 
|-
| /webgl/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="5"| MathML
| /mathml 
| Sub-Directory
| P1
| Not Started 
|-
| /mathml/data_types  
| Sub-Directory
| P3
| Not Started 
|-
| /mathml/elements
| Query
| P2
| Not Started 
|-
| /mathml/attributes
| Query
| P2
| Not Started 
|-
| /mathml/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="5"| XML
| /xml 
| Sub-Directory
| P1
| Not Started 
|-
| /xml/data_types  
| Sub-Directory
| P2
| Not Started 
|-
| /xml/elements 
| Sub-Directory
| P2
| Not Started 
|-
| /xml/attributes  
| Sub-Directory
| P2
| Not Started 
|-
| /xml/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="3"| ARIA
| /aria
| Sub-Directory
| P2
| Not Started 
|-
| /aria/attributes 
| Sub-Directory
| P2
| Not Started 
|-
| /aria/tutorials
| Query
| P3
| Not Started 
|-
| APIS
| /apis
| Sub-Directory
| P0
| Not Started 
|-
|rowspan="5"| DOM 
| /dom 
| Sub-Directory
| P0
| Not Started 
|-
| /dom/apis  
| Sub-Directory
| P1
| Not Started 
|-
| /dom/apis/methods
| Sub-Directory
| P1
| Not Started 
|-
| /dom/apis/properties
| Sub-Directory
| P1
| Not Started 
|-
| /dom/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="5"| Events 
| /events 
| Sub-Directory
| P0
| Not Started 
|-
| /events/apis  
| Sub-Directory
| P3
| Not Started 
|-
| /events/apis/methods
| Sub-Directory
| P3
| Not Started 
|-
| /events/apis/properties
| Sub-Directory
| P3
| Not Started 
|-
| /events/tutorials
| Query
| P3
| Not Started 
|-
|rowspan="12"| Javascript 
| /js  
| Sub-Directory
| P0
| Not Started 
|-
| /js/feature_detection
| Query
| P3
| Not Started 
|-
| /js/OOP
| Query
| P3
| Not Started 
|-
| /js/apis_general_context
| Query
| P3
| Not Started 
|-
| /js/data_types
| Sub-Directory
| P2
| Not Started 
|-
| /js/syntax 
| Sub-Directory
| P2
| Not Started 
|-
| /js/objects
| Sub-Directory
| P2
| Not Started 
|-
| /js/functions 
| Sub-Directory
| P2
| Not Started 
|-
| /js/statements
| Sub-Directory
| P2
| Not Started 
|-
| /js/operators 
| Sub-Directory
| P2
| Not Started 
|-
| /js/tutorials
| Query
| P3
| Not Started 
|-
| /js/libraries 
| Sub-Directory
| P3
| Not Started 
|-
| Glossary  
| /glossary  
| Sub-Directory
| P0
| Not Started 
|-
| Guides 
| /guides 
| Sub-Directory
| P0
| Not Started 
|-
| Tutorials 
| /tutorials 
| Sub-Directory
| P0
| Not Started 
|-
| Properietary 
| /properietary 
| Sub-Directory
| P0
| Not Started 
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
| [http://webplatform.org/docs/File:attribution1.png%20 Open][http://webplatform.org/docs/File:attribution2.png%20 Closed]
| 
|-
| Links
| CJ
| 
| Styling different for intra-page links, intra-wiki links, external links, and links to non-existing pages
|-
| Note callouts
| CJ
| [http://webplatform.org/docs/File:notes.png%20 Example]
| 
|-
| Language dropdown in header
| CJ
| [http://webplatform.org/docs/File:language2.png%20 Open][http://webplatform.org/docs/File:language.png%20 Closed]
| Shows current language; allows user to select new language; also allows authenticated user to create new translation
|-
| Search Box alignment
| CJ
| Done
| Size and position should align with other visual elements 
|-
| [[Template:CSS_Prefix | CSS Prefix]] callouts need to be styled
| CJ
|[http://webplatform.org/docs/File:prefix.png%20 Example]
|
|-
| Design style guide
| CJ
|[[File:Web-Platform-Style-Guide-web-1.pdf|Style Guide]]
| Provides guidlines for creating sub-properties like blog, IRC, etc.
|-
| Compatibility table styling
| CJ
|[http://webplatform.org/docs/File:prefix.png%20 Example]
| For an example, see [[css/properties/font-size]]
|-
| Stewards Page Design
| CJ
| [http://webplatform.org/docs/File:Stewards_Page.png%20 Example]
| Extensible to work for each steward, unique page for each
|-
| Landing Page Design
| CJ
| [[WPD:Design/Landing|Examples]]
| 
|-
| Static Page Design
| CJ
| [http://webplatform.org/docs/File:Static_Page_Blog.png%20 Blog Example]<br />
[http://webplatform.org/docs/File:Static_Page_QA.png%20 Q/A Example]
|
|-
| Styling for language tags in examples
| CJ
| [http://webplatform.org/docs/File:code_language.png%20 Example]
| See [[css/properties/font-size]] for an example.
|-
| Footer
| 
| 
| 
|-
| Community Badges
| 
| 
| 
|-
|rowspan="8"| Skin
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
|-
| Style the standardization flag.
| Doug
| 
| [[Template:Standardization_Status]]
|}