---
title: WPD:Creating API pages/updating template changes
---
<h2><span class="mw-headline" id="Updating_API_Listing_pages_to_use_the_new_Template:Concept_Listing">Updating API_Listing pages to use the new Template:Concept_Listing</span></h2>
<p>We have created a Template:Concept_Listing that can be called in any location on any page where you want to create a table of links and summaries. (However, it does not allow you to change where the table is produced on API_Listing pages - see below.)
</p><p>This decouples the Basic Listing Configuration section from the Template:API_Listing (which now serves only to provide the appropriate category, "API_Listings" to the page that uses it). This allows you to do landing pages that list and summarize all of the pages corresponding to the query you supply. See the Mobile Web landing page for an example.
</p><p>Note, earlier in the thread we considered providing more than the two extant options for the table header, "Page" and "API Name" - and this is a good idea, we should pursue it - but we only had bandwidth to do as much as we did for now.
</p><p>Also, the Form:API_Listing will continue to include the Template:Concept_Listing_Form_Section, which calls the Template:Concept_Listing at a specific location, so you can't put the Template:Concept_Listing anywhere you want in an API_Listing page. The PHP engine will just put it back under the Summary section when you edit the form. Here's the WebRTC API listing page for an example. If you are creating a new API_Listing page, you do it just like you used to - there is no change required in creating new API_Listing pages.
</p><p>However, we will need to update the extant API_Listing pages to use this new method, because these pages are not yet calling the new Template:Concept_Listing_Form_Section with a query. Don't worry, though, the Template:API_Listing provides for legacy usage in API_Listing pages that still pass the query to it the old way, so there should be no wreckage in extant API_Listing pages. Once we have updated all the API_Listing pages, we'll remove the legacy usage.
</p><p>To update an extant API_Listing page to use the new templates and forms:
</p>
<ol><li> Navigate to an extant API_Listing page and <b>Edit Source</b>.</li>
<li>  Under the <b>{{API_Listing</b> template call, copy the contents of the query into your buffer.
<ol><li> Select everything after the <b>Query=</b> including the brackets; for example, <b>[[Category:IndexedDB]][[Category:API_Objects]]</b>.</li>
<li> Press <b>command c</b> or <b>Ctrl c</b> or whatever.</li></ol></li>
<li> From the <b>{{API_Listing</b> call, delete the query entirely. That's the pipe character and everything up to but not including the closing <b>}}</b>.
<dl><dd> For example, delete <b>|Query=[[Category:IndexedDB]][[Category:API_Objects]]|Use_page_title=No|List_all_subpages=No</b> so that the template call now reads simply, <b>{{API_Listing}}</b></dd></dl></li>
<li> Click <b>Save page</b>. Be sure the save takes - watch out for the old session data loss bug.</li>
<li> <b>Edit</b> the page - this time with the form.</li>
<li> Under <b>Basic Listing Configuration</b>, in the <b>Query</b> field, paste the query from your buffer.</li>
<li> Click <b>Save page</b>.</li></ol>
<p>Your API_Listing is now using the new templates and forms appropriately.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:7044-0!*!*!*!*!*!*!esi=1 and timestamp 20150731183331 and revision id 21167
 -->
