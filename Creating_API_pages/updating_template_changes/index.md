---
title: updating template changes
uri: 'WPD:Creating API pages/updating template changes'

---
## Updating API\_Listing pages to use the new Template:Concept\_Listing

We have created a Template:Concept\_Listing that can be called in any location on any page where you want to create a table of links and summaries. (However, it does not allow you to change where the table is produced on API\_Listing pages - see below.)

This decouples the Basic Listing Configuration section from the Template:API\_Listing (which now serves only to provide the appropriate category, "API\_Listings" to the page that uses it). This allows you to do landing pages that list and summarize all of the pages corresponding to the query you supply. See the Mobile Web landing page for an example.

Note, earlier in the thread we considered providing more than the two extant options for the table header, "Page" and "API Name" - and this is a good idea, we should pursue it - but we only had bandwidth to do as much as we did for now.

Also, the Form:API\_Listing will continue to include the Template:Concept\_Listing\_Form\_Section, which calls the Template:Concept\_Listing at a specific location, so you can't put the Template:Concept\_Listing anywhere you want in an API\_Listing page. The PHP engine will just put it back under the Summary section when you edit the form. Here's the WebRTC API listing page for an example. If you are creating a new API\_Listing page, you do it just like you used to - there is no change required in creating new API\_Listing pages.

However, we will need to update the extant API\_Listing pages to use this new method, because these pages are not yet calling the new Template:Concept\_Listing\_Form\_Section with a query. Don't worry, though, the Template:API\_Listing provides for legacy usage in API\_Listing pages that still pass the query to it the old way, so there should be no wreckage in extant API\_Listing pages. Once we have updated all the API\_Listing pages, we'll remove the legacy usage.

To update an extant API\_Listing page to use the new templates and forms:

1.  Navigate to an extant API\_Listing page and **Edit Source**.
2.  Under the **{{API\_Listing** template call, copy the contents of the query into your buffer.
    1.  Select everything after the **Query=** including the brackets; for example, **[[Category:IndexedDB]][[Category:API\_Objects]]**.
    2.  Press **command c** or **Ctrl c** or whatever.

3.  From the **{{API\_Listing** call, delete the query entirely. That's the pipe character and everything up to but not including the closing **}}**.
    <dl>
    <dd>
    For example, delete **|Query=[[Category:IndexedDB]][[Category:API\_Objects]]|Use\_page\_title=No|List\_all\_subpages=No** so that the template call now reads simply, **{{API\_Listing}}**
    </dd>
4.  Click **Save page**. Be sure the save takes - watch out for the old session data loss bug.
5.  **Edit** the page - this time with the form.
6.  Under **Basic Listing Configuration**, in the **Query** field, paste the query from your buffer.
7.  Click **Save page**.

Your API\_Listing is now using the new templates and forms appropriately.
