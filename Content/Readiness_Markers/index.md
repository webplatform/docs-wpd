Readiness markers indicate the state of readiness of a page:

===Ready to Use===
A document should be marked Ready to Use if a developer who is looking for reference material on this topic can randomly land on this page and get complete, accurate information. The information on a Ready to Use page is not outdated, and it's not incomplete in a way that would make the information confusing. Much of the documentation on webplatform.org will need to be continuously be revised and updated as standards and techniques change, so Ready to Use pages don't have to always be 100% perfect. They may need minor errors or quick updates.  Hopefully those kinds of edits are simple done as soon as the need for an edit is discovered. In that case, switching the readiness status of the page in a more complex workflow process isn't needed.

===Almost Complete===
A document should be marked Almost Complete if it's 80% ready, but still needs something that's clearly missing or inaccurate.  Almost Complete might be used when the descriptions are good, but there are no examples. Or when the editing that humans can do is complete, but there's still something else that needs to be coded in the system to make the pages ready — such as connecting the compatibility tables. This could be used as a way to mark a group of pages for review if an initiative needs such a tool, as a kind of Q/A stage. Or this status might not be used at all; pages can go straight from In Progress to Ready to Use if the circumstances warrant it.

===In Progress===
A document should be marked In Progress if work on it has officially begun, but it's not close to being ready yet. This marker will tell developers who may stumble across the page — hey, don't trust this documentation yet: It's not a reliable source of information, it's a page that's being heavily rewritten. Any page that's more than 10%, but less than 80% done should be marked In Progress. It doesn't matter whether there is active work being done on it currently or not. 

===Coming Later===
A document should be marked Coming Later when it's just an idea. This can be used when someone has created a page, with a URL and a title, but not much else. It should also be used when content is imported from an outside source, but has not been looked at by WPD contributors or restructured for our system yet. 

==Templates==

The readiness marker system is now live on the main wiki.  CSS styling still to come.

* http://docs.webplatform.org/wiki/Property:State  
The State property defines the readiness state property, and contains definitions of each value (slightly shorter versions of the ones from Jen's email) and links to search pages for each value.  For now, this is the page you get to when you click on the readiness-related link in the form or main article page.    

I would still like to create a more detailed page within the WPD namespace, something that could be incorporated within the contributor's guide.  It would discuss readiness as a concept and give more detail to the definitions, probably reusing some of the existing discussion of alpha/beta stages.  But for now we have basic definitions on the property page.

* http://docs.webplatform.org/wiki/Property:State_Details
The State Details property will contain any editorial notes related to the page and the reason it was given a certain state.  Nothing prints on the final "View" mode of the article, but by saving the information as a property they can be accessed by search functions (the above link will have a list of all articles with a value set).  

Although the property is new, it reuses the "Editorial Notes" form field from the old flags template, which means that any custom editorial notes should be preserved (although it's a little messy, because most of them used their own templates which inject html code).

* http://docs.webplatform.org/wiki/Template:Flags_Form_Section
The old flags form section template has been reused, so that all pages that previously allowed you to set flags now allow you to set a readiness state.  The revised template has three elements: readiness state, state details/editorial notes, and checked out.  Edit any reference page to see what it looks like in action.

*  http://docs.webplatform.org/wiki/Template:Flags
Likewise, the old Flags template has been used to print the readiness markers.  Any pages which previously had the option to show flags under the title will instead show the readiness statement (if a value has been set).

The state value is printed to the page in the following format:
<syntaxhighlight>
<div class="note readiness-state Almost_Done"> 
<p>This article is <a href="/wiki/Property:State" title="Property:State">Almost Done.</a>
</p>
</div>
</syntaxhighlight>

The "note" class is responsible for the current yellow-box display.  The "readiness-state" and state-specific class will be used for the final CSS.  The state-specific classes are created from the property values by replacing spaces with "_", so they are: "Ready_to_Use", "Almost_Done", "In_Progress", "Coming_Later", "Out_of_Date".  (The "Unreviewed" value currently never results in a div being added to the page.)

* Property:Content_quality_flag is still used for the automatically-set flags Needs Summary, Examples Needed, and Compatibility Incomplete.  I'll re-write the property page (and the one for high-level issues) when I get to writing up that article on readiness in general.