---
title: Step 6: Author or upload new content
notes:
  - 'Update documentation about Compability'
readiness: 'Out of Date'
summary: 'This is Step 6 of the Editor''s Guide.'
tags:
  - Basic
  - Pages
uri: 'WPD:Editors Guide/step 6 author or upload new content'

---
## <span>Summary</span>

This is Step 6 of the Editor's Guide.

## <span>Step 6. Author or upload new content</span>

### <span>Determine if your content is appropriate to add to this wiki</span>

-   Use the [Advanced Search page](http://docs.webplatform.org/w/index.php?title=Special:Search) to verify that the topic does not already exist.
-   Refer to the [Pillars page](/WPD:Policy/Pillars) to learn about the goals of WebPlatform.org and review the three pillars governing WebPlatform.org.

### <span>Let the team know that you are adding new content</span>

-   See [Step 2 of the Editor's Guide](/WPD:Editors_Guide/step_2_communicate_with_the_online_community) to find out how to ask questions online.

### <span>Author new content using the correct site formatting and standards</span>

-   Visit [Step 5 of the Editor's Guide](/WPD:Editors_Guide/step_5_update_existing_content) to learn how to format pages using the wiki syntax and apply appropriate syntax highlighting to code snippets.
-   Follow the conventions outlined in the [Yahoo style guide](http://styleguide.yahoo.com/).

### <span>Create a new page in the wiki</span>

-   In most cases, you can use the form on the [New Page page](/WPD:New_Page).
-   If you are authoring tutorials and concept articles, follow the [Tutorial and concept articles page](/WPD:Content/Tutorials_and_concept_articles).
-   If you are authoring reference documentation, see the [Reference articles page](/WPD:Content/Reference_articles).
-   If you are authoring API documentation, read the [Creating API documentation page](/WPD:Creating_API_pages).

### <span>Choose where to create the new page</span>

-   Visit the [Topic hierarchy page](/WPD:Content/Topic_Hierarchy) to learn how the pages in this wiki are structured.
-   See the [Architecture page](/WPD:Architecture) to choose a location to save the new page you are creating.
-   If you are not sure which section to create the new page, see [Step 2 of the Editor's Guide](/WPD:Editors_Guide/step_2_communicate_with_the_online_community) to learn how to ask for guidance.

### <span>Create valid URLs for new pages</span>

Next, go to the [New Page page](/WPD:New_Page) and create a new page using one of the defined content page templates. When you create pages, remember that the text you enter in the path text box becomes the URL for the new page. Also note that the page URL does not need to match the visible page title.

For example, a page with the URL: eventsource\_basics can have an internal title: Streaming updates with server-sent events. The goal is to keep URLs short, descriptive, and unique.

-   Do not capitalize words in a URL unless absolutely vital for syntax correctness. For example, if you are authoring an article about user media, you can enter: usermedia; for an article specifically about the getUserMedia method, you might instead enter: getUserMedia.
-   Use spaces, not underscores, to separate words in a URL, because underscores are generated automatically in place of spaces when the page is created. For example, if you are creating a new article about the HTML5 audio tag, you can enter: audio tag and the generated URL will be: audio\_tag.
-   Do not use other punctuation, such as dashes or parentheses, in a URL. This is especially important because adding punctuation in URLs causes major site issues.
-   Do not use articles (the, a, an) in URLs unless absolutely necessary.

### <span>Check for broken links</span>

-   Before moving existing pages, identify [pages that contain links to the existing document](http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace) and then update the links in those pages to use the new URL you have just created.

### <span>Check features for cross browser compatibility</span>

*Note* This feature has been reworked, refer to [the Compability template](https://docs.webplatform.org/wiki/Template:Compatibility) to learn how you can include table in a page.

### <span>Topics and topic clusters</span>

Generally, we use topics to describe articles at their lowest level of granularity - what the article is about. An article may have more than one topic. We use topic clusters to group articles of similar topics. Topic clusters produce a list of related topics in the See Also section. The following sections describe the use cases of topics and topic clusters.

### <span>Topics use cases</span>

Use topics to describe the article for the following purposes. Note that these use cases are not mutually exclusive, and you can use topics for either or both.

#### <span>Basic meta data</span>

Topics describe the article's content with keywords. Mark as many as apply *usefully*. Too much meta data can blur the picture worse than too little. The topic keywords have several uses, such as search engine optimization, and effectively describe the content taxonomy. This taxonomy has multiple facets. For example, the CSS-Regions API is an API (the content's purpose) and it is about CSS (the content's subject matter); furthermore, it is specifically about CSS-Regions. But the CSS-Regions topic tag is more than general meta data, it is used specifically to delineate structure and navigation. See next.

#### <span>API Basic Listing Configuration Query</span>

Use a topic to describe the article within the context of its template type (these are described in the [WPD:New\_Page](/WPD:New_Page) page). That is, if the page is for an API object (which uses the API\_Object template), and the article is about the CSS-Regions API, then the topic checkbox to check is "CSS-Regions." This allows you to specify the query, "[[Category:CSS-Regions]][[Category:API\_Objects]]" in the API\_Listing page that produces a summary table of all the API objects. This query says, "fetch me the pages of the CSS-Regions topic that are also API\_Object pages." This means that for every API there must be a topic specific to that API.

Notice that the query does not select for the more general Category:CSS. If there were other CSS-related JavaScript APIs, let's say CSS-Overlay (this is fake), and if both the CSS-Regions and CSS-Overlay API\_Listing pages queried for Category:CSS, all of the objects from both APIs would appear in each API's summary table. The way to prevent such duplication from happening is to create a discrete topic for all of the API\_Object pages within one API\_Listing.

See [Creating API pages](/WPD:Creating_API_pages#Object_listing_page_content) for more information. See [WPD:Topics](/WPD:Topics) for how to create new topics.

### <span>Topic clusters use case</span>

To produce a list of articles of related content in the See Also section, use a topic cluster. The key here is to get articles from across the many domains of the wiki - tutorials, concepts, APIs, HTML elements, and so on. Sometimes these articles will share a common term, like "WebRTC." But sometimes the common term won't be obvious.

For example, with three Timing APIs - [apis/navigation\_timing](/apis/navigation_timing), [apis/resource\_timing](/apis/resource_timing), [apis/user\_timing](/apis/user_timing) - you might think these should share the "Timing" topic cluster. But then your topic cluster would miss all of the articles about optimization, debugging, and performance. Probably the best topic cluster to use in this case is "Performance."

**Careful!** It is easy to abuse topic clusters by tagging too many articles for the same topic cluster. Doing so only creates a long list of unnecessary links. For example, API object members (events, methods, and properties) do not need to be in the topic cluster; only the API object needs to be in the topic cluster. Furthermore, avoid using large-scope topic clusters like "CSS" - again, all you'll get is a huge list of unrelated items.

To create a new topic cluster, add it to the list in [Property:Topic\_Cluster](/Property:Topic_Cluster).

### <span>Update the status of compatibility</span>

If you complete the compatibility tables on a page (for both desktop and mobile browsers), you can deselect the Compatibility Incomplete check box in the Content section just below the page title, to the left of the text in the English version.

If you are editing or authoring a page and you feel that compatibility information is not needed (and the page is currently [listed as a page with missing compatibility information](http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace=) because the template flags compatibility as missing by default), you can check the box immediately under the Compatibility section header to indicate that this section is not needed (and ensure it will not appear on the site). Be sure to also deselect the Compatibility Incomplete check box near the top of the page as described above.

Your final summary (commit) comment should mention if you have changed the status of the compatibility information.

### <span>Upload and link images or other assets to pages</span>

Visit [Step 7 of the Editor's Guide](/WPD:Editors_Guide/step_7_prepare_and_upload_assets_for_articles) to learn how to prepare and upload image files and other assets. Once a file is uploaded, you can add links to it.

### <span>Save your work</span>

After completing your edits on a page, enter a summary of your changes in the Summary field, check the box for a minor edit if you only tweaked existing information, click the Show preview button to review your work (recommended), and then click Save page button to save your changes.

**Note**: If you have been editing for a while without saving, your session information may be stale, and you may be presented with the following warning message:

**Sorry! We could not process your edit due to a loss of session data. Please try again....** (along with a deceptively updated preview of your unprocessed new version, and the edited source).

When you see this error, click the Save page button again. In most cases, simply resubmitting the form will work (because the first attempt refreshes your session, and the second attempt enables the submission to process).

### <span>Add exceptions</span>

If you want to mention any outstanding issues, items or questions about the page, add the following tag on the page with a message:

{{TODO | [This is a description of items still missing on this page.] }}

### <span>Get additional information about how templates work</span>

This wiki uses templates to format and standardize page content. Although it is not necessary for contributing, you can get the granular details about how the wiki works behind the scenes.

-   If you want to delve into how the templates work, check out the [Implementation Patterns page](/WPD:Implementation_Patterns).

