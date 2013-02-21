{{Page_Title|Step 6: Author or upload new content}}
{{Flags}}
{{Summary_Section|This is Step 6 of the [[WPD:Editors_Guide|Editor's Guide]].}}
{{Basic Page}}
==Step 6. Author or upload new content==
===Determine if your content is appropriate to add to this wiki===
* Use the [http://docs.webplatform.org/w/index.php?title=Special:Search Advanced Search page] to verify that the topic does not already exist. 
* Refer to the [[WPD:Policy/Pillars| Pillars page]] to learn about the goals of WebPlatform.org and review the three pillars governing WebPlatform.org.
===Let the team know that you are adding new content=== 
* See [[WPD:Editors_Guide/step_2_communicate_with_the_online_community|Step 2 of the Editor's Guide]] to find out how to ask questions online.
===Author new content using the correct site formatting and standards=== 
* Visit [[WPD:Editors_Guide/step_5_update_existing_content|Step 5 of the Editor's Guide]] to learn how to format pages using the wiki syntax and apply appropriate syntax highlighting to code snippets.
* Follow the conventions outlined in the [http://styleguide.yahoo.com/ Yahoo style guide].
===Create a new page in the wiki===
* In most cases, you can use the form on the [[WPD:New_Page| New Page page]].
* If you are authoring tutorials and concept articles, follow the [[WPD:Content/Tutorials_and_concept_articles  | Tutorial and concept articles page]].
* If you are authoring reference documentation, see the [[WPD:Content/Reference_articles | Reference articles page]].
* If you are authoring API documentation, read the [[WPD:Creating_API_pages | Creating API documentation page]].

===Choose where to create the new page===
* Visit the [[WPD:Content/Topic_Hierarchy| Topic hierarchy page]] to learn how the pages in this wiki are structured.
* See the [[WPD:Architecture|Architecture page]] to choose a location to save the new page you are creating.
* If you are not sure which section to create the new page, see [[WPD:Editors_Guide/step_2_communicate_with_the_online_community|Step 2 of the Editor's Guide]] to learn how to ask for guidance.
===Create valid URLs for new pages===
Next, go to the [[WPD:New_Page | New Page page]] and create a new page using one of the defined content page templates. When you create pages, remember that the text you enter in the path text box becomes the URL for the new page. Also note that the page URL does not need to match the visible page title. 

For example, a page with the URL: eventsource_basics can have an internal title: Streaming updates with server-sent events. The goal is to keep URLs short, descriptive, and unique.

*Do not capitalize words in a URL unless absolutely vital for syntax correctness. For example, if you are authoring an article about user media, you can enter: usermedia; for an article specifically about the getUserMedia method, you might instead enter: getUserMedia.
*Use spaces, not underscores, to separate words in a URL, because underscores are generated automatically in place of spaces when the page is created. For example, if you are creating a new article about the HTML5 audio tag, you can enter: audio tag and the generated URL will be: audio_tag.
*Do not use other punctuation, such as dashes or parentheses, in a URL. This is especially important because adding punctuation in URLs causes major site issues.
*Do not use articles (the, a, an) in URLs unless absolutely necessary.
===Check for broken links===
* Before moving existing pages, identify [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace pages that contain links to the existing document] and then update the links in those pages to use the new URL you have just created.

===Check features for cross browser compatibility===
Compatibility tables provide details about which CSS, HTML, and JavaScript  features and APIs are supported by which browsers, itemized by browser version. These tables are built into the templates with the header: Compatibility (with separate sections for desktop and mobile). Here is a screenshot of a compatibility table:

[[Image:compatibility_table.png|alt=Screenshot of a compatibility table.]]

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

There is a third table in the compatibility section for Compatibility Notes.  Use this to cover anything that cannot be covered just by indicating yes/no  and a version number.

===Topics and topic clusters===

Generally, we use topics to describe articles at their lowest level of granularity - what the article describes. An article may have more than one topic. We use topic clusters to group articles of similar topics. Topic clusters allow you to produce a list of related topics in the See Also section. The following sections describe the use cases of topics and topic clusters.

===Topics use cases===

====API Basic Listing Configuration Query====

Use '''topics''' to describe the article within the context of its template type (these are described in the [[WPD:New_Page]] page). That is, if the page is for an API object (which uses the API_Object template), and the article is about the CSS-Regions API, then the topic checkbox to check is "CSS-Regions." This allows you to specify the query, "<nowiki>[[Category:CSS-Regions]][[Category:API_Objects]]</nowiki>" in the API_Listing page that produces a summary table of all the API objects. This query says, "fetch me the pages of the CSS-Regions topic that are also API_Object pages." See [[WPD:Creating_API_pages#Object_listing_page_content|Creating API pages]] for more information.



===Update the status of compatibility===
If you complete the compatibility tables on a page (for both desktop and mobile browsers), you can deselect the Compatibility Incomplete check box in the Content section just below the page title, to the left of the text in the English version.  

If you are editing or authoring a page and you feel that compatibility information is not needed (and the page is currently [http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace= listed as a page with missing compatibility information] because the template flags compatibility as missing by default), you can check the box immediately under the Compatibility section header to indicate that this section is not needed (and ensure it will not appear on the site). Be sure to also deselect the Compatibility Incomplete check box near the top of the page as described above.

Your final summary (commit) comment should mention if you have changed the status of the compatibility information. 

===Upload and link images or other assets to pages===
Visit [[WPD:Editors_Guide/step_7_prepare_and_upload_assets_for_articles| Step 7 of the Editor's Guide]] to learn how to prepare and upload image files and other assets. Once a file is uploaded, you can add links to it. 

===Save your work===
After completing your edits on a page, enter a summary of your changes in the Summary field, check the box for a minor edit if you only tweaked existing information, click the Show preview button to review your work (recommended), and then click Save page button to save your changes.

{{Note|If you have been editing for a while without saving, your session information may be stale, and you may be presented with the following warning message:

'''Sorry! We could not process your edit due to a loss of session data. Please try again....''' (along with a deceptively updated preview of your unprocessed new version, and the edited source). 

When you see this error, click the Save page button again. In most cases, simply resubmitting the form will work (because the first attempt refreshes your session, and the second attempt enables the submission to process).}}

===Add exceptions===
If you want to mention any outstanding issues, items or questions about the page, add the following tag on the page with a message:

<nowiki>
{{TODO | [This is a description of items still missing on this page.] }}</nowiki> 

===Get additional information about how templates work===
This wiki uses templates to format and standardize page content. Although it is not necessary for contributing, you can get the granular details about how the wiki works behind the scenes. 
* If you want to delve into how the templates work, check out the [[WPD:Implementation_Patterns| Implementation Patterns page]].
{{Notes_Section}}
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}