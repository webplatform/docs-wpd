{{Page_Title|Step 6: Author or upload new content}}
{{Flags}}
{{Summary_Section|This is Step 6 of the [[WPD:Editors_Guide|Editor's Guide]].}}
{{Basic Page}}
==Step 6. Author or upload new content==
===Determine if your content is appropriate to add to this wiki===
* Refer to the [[WPD:Policy/Pillars| Pillars page]] to learn about the goals of WebPlatform.org and review the three pillars governing WebPlatform.org.
===Let the team know that you are adding new content=== 
* See [[WPD:Editors_Guide/step_2_communicate_with_the_online_community|Step 2 of the Editor's Guide]] to find out how to ask questions online.
===Author new content using the correct site formatting and standards=== 
* Visit [[WPD:Editors_Guide/step_5_update_existing_content|Step 5 of the Editor's Guide]] to learn how to format pages using the wiki syntax.
* Follow the conventions outlined in the [http://styleguide.yahoo.com/ Yahoo style guide].
===Create a new page in the wiki===
* In most cases, you can use the form on the [[WPD:New_Page| New Page page]].
* If you are authoring tutorials and concept articles, follow the [[WPD:Content/Tutorials_and_concept_articles  | Tutorial and concept articles page]].
* If you are authoring reference documentation, see the [[WPD:Content/Reference_articles | Reference articles page]].
* If you are authoring API documentation, read the [[WPD:Creating_API_pages | Creating API documentation page]].
===Check for broken links===
* Before creating or moving pages, identify [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace pages that contain links to the existing document] and then update the links in those pages to use the new URL.

===Choose where to create the new page===
* Visit the [[WPD:Content/Topic_Hierarchy| Topic hierarchy page]] to learn how the pages in this wiki are structured.
* See the [[WPD:Architecture|Architecture page]] to choose a location to save the new page you are creating.
===Check features for cross browser compatibility===
Compatibility Information tables provide details about which (CSS/HTML/JavaScript) features/APIs are supported by which browsers, by version. These tables are built into the templates with the header: Browser Compatibility (with separate tabs for desktop and mobile). Here is an example of a Compatibility Information table:

[[File:compatibility_table.png]]

The tables are automatically flagged as incomplete, which causes them appear on dynamic [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace= list of pages with missing compatibility information].

For the purposes of this site, the support for a technology in modern browsers is most important. If a property was supported in IE 4 or Safari 1, it is not as critical as stating compatibility with the most recent browser versions. 

For each item, note which browser version was the first to provide complete support.  If only partial support is currently provided, note that by adding the word (partial) after the version number.

* Review the following cross-compatibility online resources to learn which technologies are supported in which browsers:
* [http://caniuse.com/ www.caniuse.com]
* [http://www.quirksmode.org/compatibility.html Compatibility section on www.quirksmode.org]
* [http://developer.mozilla.org Mozilla Developer Network site]

Mozilla Developer Network has agreed to allow contributors to copy the basic facts (browser version numbers, yes/no/partial on support) without attribution. When researching compatibility facts on other online resources, be sure to  follow the [http://docs.webplatform.org/wiki/WPD:External_Attribution Attribution guidelines].

Each element is either supported or not (by selecting the radio buttons for yes, no, and unknown). If an item is supported, there is a minimum browser version that supports it (and presumably all higher versions will also support it).

For some elements, there may be sub-elements or features that need to called out individually.  For these, after you have covered the Basic Support, you can click the "Add Another" button to add additional rows to the table.

To see an example of a multiple row Compatibility Information table, check out the [http://docs.webplatform.org/w/index.php?title=html/elements/audio Audio tag] which contains separate rows for the various audio codecs covered in the HTML5 spec, since support differs significantly across browsers.

Additional rows should be sorted by name.  Use the drag handles to the right of the "Remove" button to move an item up or down in the table.

===Compatibility Notes===
There is a third table in the compatibility section for Compatibility Notes.  Use this to cover anything that cannot be covered just by indicating yes/no  and a version number. Just click "Add another" to insert a row.

===Save your work===
After completing your edits on a page, enter a summary of your changes in the Summary field, check the box for a minor edit if you only tweaked existing information, click the Show preview button to review your work (recommended), and then click Save page button to save your changes.

{{Note|If you have been editing for a while without saving, your session information may be stale, and you may be presented with the following warning message:

'''Sorry! We could not process your edit due to a loss of session data. Please try again....''' (along with a deceptively updated preview of your unprocessed new version, and the edited source). 

Most of the time, you can click the Save page button again. In most cases, simply resubmitting the form will work (because the first attempt refreshes your session, and the second attempt enables the submission to process).}}

===Add exceptions===
If you feel that the Compatibility Information on a page is now complete (for both desktop and mobile browsers), you can deselect the Compatibility Incomplete check box in the Content section just below the page title (the check box is to the left of the text in the English version).  

If you feel that compatibility information is not needed for this topic (and the page was on the list because the template flags it as missing by default), you can check the box immediately under the "Compatibility" section header to indicate that this section is not needed (and ensure it will not appear on the site). Be sure to also deselect the Compatibility Incomplete check box near the top of the page.

Your final summary (commit) comment should mention if you have changed the status of the compatibility information. 

If you want to mention any outstanding issues, items or questions about the page, add the following tag on the page with a message:

<nowiki>
{{TODO | [This is a description of items still missing on this page.] }}</nowiki> 

===Get additional information about how templates work===
This wiki uses templates to format and standardize page content. Although it is not necessary for contributing, you can get the granular details about how the wiki works behind the scenes. 
* If you want to delve into how the templates work, check out the [[WPD:Implementation_Patterns| Implementation Patterns page]].