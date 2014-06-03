=Quality Assurance & Readiness Review <br/>(aka QA Sprint), <br/>June 2014=

==Overview==
As part of the progression of Webplatform.org to Beta stage (see the [[WPD:Project Status | Project Status]] or [[WPD:Projects/Beta Requirements | Beta requirements]] pages), we need to assign [[Property:State | readiness state properties]] to every reference article.  Once individual articles have markers of their quality, we can remove the "Web Platform Docs is in alpha" warning from every page.

As this will require a manual review of every page by experienced contributors, this is also a good time to do other quick and simple clean-up and quality assurance (QA) tasks that can only be done manually.

==Proposed QA Checklist==

The following is a list of tasks which have been suggested for this review.  Any additions/concerns should be posted to the mailing list or discussed on IRC.  A final version will be agreed on hopefully in the 3 June 2014 teleconference (and if not, by the following week).

For most pages (those for which the "Edit" button opens up an editing form):

# Assign a readiness state.  [[WPD:Templates/Readiness_Markers | More about readiness states (requires clean-up)]]
# Add any details about readiness/what is required to the editorial notes box.
# For DOM method pages, assign index values to the parameter entries in order to get the correct syntax to display, as [http://lists.w3.org/Archives/Public/public-webplatform/2014May/0026.html described in this email post].
# Confirm that the new compatibility tables are pulling in the correct data (Doug Schepers is going to give us more information about this once the import from MDN happens later this week).

For pages that don't currently have a page template/default form (the "Edit" button opens a text box):

# Make sure that the first line in the code is the <code><nowiki>{{Page Title}}</nowiki></code> template; if the page currently has an h1 heading (surrounded by one '=' on either side) that is different from the last part of the file path, add it as a parameter to the template, like <code><nowiki>{{Page Title | Text to use as title}}</nowiki></code>
# Manually add the line <code>{{!}}State=Coming Later</code> to the <code><nowiki>{{Flags}}</nowiki></code> template (or one of the other state values, although I'm fairly certain any pages that don't have default forms will be "Coming Later").  If there is no such template, create it like <code><nowiki>{{Flags|State=Coming Later}}</nowiki></code>.  If there is a Flags template, be sure not to delete any existing parameters.

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

Possible additions (if we have enough volunteers that we can afford to spend more time per page):

* Ensure that every page has a summary section.


==List of Volunteers==

'''Please add your name to this list if you're willing to contribute.'''  The amount of work that can be done will depend on the number of people we have.  There are 4400+ articles to review, it would be nice to have 20+ people tackling them; more people means fewer articles each.  However, we are not trying to solicit brand new contributors for this, like in a DocSprint.  Participants must be familiar with the mediawiki structure and understand the content quality expectations.

# shepazu
# renoirb
# jensimmons
# julee
# eliot
# AmeliaBR
# eliezerb
# garbee
# frozenice
# Michaela

<!-- Your name here... -->

==Plan of Attack==

Divide up by main content section (HTML/CSS/Javascript/etc.) and then divide up each category index into alphabetical chunks of equal numbers of articles.  

Any more detailed plans welcome...

==Timeline==

* Comments and volunteers ASAP, preferably by 3 June 2014, definitely before 10 June 2013.
* Work completed by June 24 (?) Or can we do it by June 17 ?