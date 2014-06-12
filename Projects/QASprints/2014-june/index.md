=Quality Assurance & Readiness Review <br/>(aka QA Sprint), <br/>June 2014=

==Overview==
As part of the progression of Webplatform.org to Beta stage (see the [[WPD:Project Status | Project Status]] or [[WPD:Projects/Beta Requirements | Beta requirements]] pages), we need to assign [[Property:State | readiness state properties]] to every reference article.  Once individual articles have markers of their quality, we can remove the "Web Platform Docs is in alpha" warning from every page.

As this will require a manual review of every page by experienced contributors, this is also a good time to do other quick and simple clean-up and quality assurance (QA) tasks that can only be done manually.

==Review Tasks==

The following is a list of tasks which have been suggested for this review.  <!-- Any additions/concerns should be posted to the mailing list or discussed on IRC.  A final version will be agreed on hopefully in the 3 June 2014 teleconference (and if not, by the following week). -->

# Assign a readiness state.  [[WPD:Content/Readiness_Markers | More about readiness states]]
# <del>Add any details about readiness/what is required to the editorial notes box.</del>
# For DOM method pages, assign index values to the parameter entries in order to get the correct syntax to display, as [http://lists.w3.org/Archives/Public/public-webplatform/2014May/0026.html described in this email post].
# For pages without a default form, ensure that they have the basic <code><nowiki>{{Page Title}}</nowiki></code> template to make them searchable by name and path.
# <del>Confirm that the new compatibility tables are pulling in the correct data (Doug Schepers is going to give us more information about this once the import from MDN happens later this week).</del>
# For almost-done pages, check that the W3C status icon is correct.
# <del> Ensure that every page has a summary section.</del>

==Checklist==

We have a lot of pages to get through, so this checklist has been designed to make the assessment quick and consistent.  Follow the decision tree until you reach a readiness state.  For some pages there are extra to-do lists, given below.

===Decision Tree for all pages===
# Does the page have an editing form?
#;	NO:	
#:*		follow basic templates to-do list.  
#:*		Readiness = COMING LATER.   
# Is the page in a language other than English?
#;	YES:  leave Readiness = UNREVIEWED
# Is the page an obvious mistake or deletion candidate?
#;	YES:  
#:*		add an explanation to the Details field (the text box under the Readiness State selector in the form), if it isn't already there
#:*		delete all content from the page if it is particularly objectionable (It would be preferable if you don't delete the page even if you have permission, as this will throw off the search listings used to assign articles)
#:*		leave Readiness = UNREVIEWED
# Is this a DOM method page?  
#;	YES:	
#:*		follow DOM method to-do list.
#:*		continue with the checklist.
# Is there substantial content on the page?
#; ''For REFERENCE DOCS:'' 
#: Are there fewer than 3 of the following sections?
#:*		Summary
#:*		Values for info tables / syntax (if relevant)
#:*		Written description / notes
#:*		Examples
#:*		Specifications 
#:*		Compatibility
#;  ''For TUTORIAL/CONCEPT pages:''  
#:   Is this obviously a stub page without much content?
#;	YES: Readiness = COMING LATER
# Is there a good summary?
#;	NO: Readiness = IN PROGRESS
# Is there obvious bias towards one software (IE, Firefox)?  
#;	YES: Readiness = IN PROGRESS
# Is there any major content quality problem (spelling/grammar/formatting)?
#;	YES: Readiness = IN PROGRESS
# Is there still a lot of work to do?
#; ''For REFERENCE DOCS:'' 
#:   How many of the sections from (3) are missing?
#;	2-3 sections missing: Readiness = IN PROGRESS
#;	1 section missing: Readiness = ALMOST READY
#;	All sections included: continue to next step
#;   ''For TUTORIALS/CONCEPT pages:''
#:   Are there signs that this is half-done?
#;	YES: Readiness = IN PROGRESS
#;	NO: continue to next step
# Is there a circular W3C icon on the page?
#;	YES: Follow the Standardization Status to-do list.
# Are there any other problems you can see at a glance?  
#* Could there obviously be better/more detailed explanations? 
#* Do you have any concerns about whether the content is accurate and up-to-date?
#;	YES: Readiness = ALMOST READY
#;	NO, everything looks good: Readiness = READY TO USE

===DOM Method To-Do List===
# Does the syntax block have the words "see parameter list" insted of parameters?
#;	YES: Open the editing form, and assign consecutive integer values (0,1,2,3...) to the "Argument Index" field for each parameter (in the order they are given in the page)
# Continue with the readiness checklist

===Standardization Status To-Do List===
# In the edit form, ensure that the value for Standardization Status matches the most recent value in the Specifications table.
# Continue with the readiness checklist

===Basic Templates To-Do List===
For pages that don't currently have a page template/default form (the "Edit" button opens a text box):

# Make sure that the first line in the code is the <code><nowiki>{{Page Title}}</nowiki></code> template.
# If the page currently has an h1 heading (surrounded by one '=' on either side), add it as a parameter to the template, like <code><nowiki>{{Page Title | Text to use as title}}</nowiki></code>; delete it from the main text and don't include the `=` in the template parameter value.
# Manually add the line <code>{{!}}State=Coming Later</code> to the <code><nowiki>{{Flags}}</nowiki></code> template (or one of the other state values, although I'm fairly certain any pages that don't have default forms will be "Coming Later").  
#* If the flags template isn't there, add it as <code><nowiki>{{Flags|State=Coming Later}}</nowiki></code>.  
#* If there is a Flags template, be sure not to delete any existing parameters.

The bare minimum will look like
<pre>
   {{Page Title}}
   {{Flags|State=Coming Later}}
</pre>

An example with a custom title and existing flag information will look like
<pre>
   {{Page Title|multiply()}}
   {{Flags
   |State=Coming Later
   |High-level issues=Needs Topics, Missing Relevant Sections, Data Not Semantic, Unreviewed Import
   |Content=Incomplete, Not Neutral, Compatibility Incomplete, Examples Best Practices, Cleanup
   }}
</pre>




==List of Volunteers==

'''Thanks for everyone who volunteered.'''  If anyone else wants to help, get in touch with one of the people on the list and ask them if they need help on their assigned articles.

<del>'''Please add your name to this list if you're willing to contribute.'''  The amount of work that can be done will depend on the number of people we have.  There are 4400+ articles to review, it would be nice to have 20+ people tackling them; more people means fewer articles each.  However, we are not trying to solicit brand new contributors for this, like in a DocSprint.  Participants must be familiar with the mediawiki structure and understand the content quality expectations.</del>

If you indicate topic areas you are comfortable with, I'll try to make most of your assigned articles in that domain, but there will be some overlap and I'm assigning things alphabetically (by file path) since that's how search results are ordered.

# shepazu  (SVG, etc)
# renoirb
# jensimmons (CSS & HTML)
# julee
# eliot (Javascript)
# AmeliaBR (SVG, whatever's needed)
# eliezerb
# garbee
# frozenice (HTML & DOM)
# Michaela (CSS & HTML)
# Paulv
# emerson (HTML/CSS/DOM)
# brianjhong (HTML & CSS)
# Rob^_^ (any)
# Hiroki
# Roberto
<!-- Your name here... -->

==Article Blocks==

The following article lists have been assigned to each volunteer:

; First name
:* [[/WPD:Editors Guide/step 2 communicate with the online community/ko]] to [[apis/filesystem/Entry/isDirectory]]
:* [{{fullurl:Special:Ask|q={{urlencode:[[State::+]]}}&offset=0&limit=275&po={{urlencode:? State ?State Details}}&mainlabel={{urlencode:File Path}}&intro={{urlencode:Here are your assigned articles:}}&outro={{urlencode:Thanks for helping with the QASprint!}}&default={{urlencode:There was an error with the search...}}&class={{urlencode:sortable wikitable smwtable}} }} search page]
:* [http://docs.webplatform.org/w/index.php?title=Special%3AAsk&q=%5B%5BState%3A%3A%2B%5D%5D&po=%3FState%0D%0A%3FState+Details%0D%0A&eq=yes&p%5Bformat%5D=broadtable&sort_num=&order_num=ASC&p%5Blimit%5D=275&p%5Boffset%5D=0&p%5Blink%5D=all&p%5Bsort%5D=&p%5Bheaders%5D=show&p%5Bmainlabel%5D=&p%5Bintro%5D=&p%5Boutro%5D=&p%5Bsearchlabel%5D=Tthanks+for+helping+with+the+QASprint%21&p%5Bdefault%5D=%28something+is+wrong+with+the+search%29&p%5Bclass%5D=sortable+wikitable+smwtable&eq=yes# search page]

==Plan of Attack==

If you need help, [[WPD:Community#Chat_with_us_on_IRC | ask on IRC ]].  If you can't complete your assigned tasks, send a note to the email list clearly indicating what range of articles still needs to be done, so that other people can take over.

==Timeline==

* <del>Comments and volunteers ASAP</del>
* Articles to be assigned Thursday June 12, 2014
* Work completed by July 1

==Progress==

Current Article Count:
* Needs Review:  {{#ask: [[State::Unreviewed]] | format=count}} articles
* Readiness Assessed: {{#ask: [[State::!Unreviewed]] | format=count}} articles

(You can see the counts by readiness state, with links to all articles given that state, on the [[Property:State]] page.)