==Updating API_Listing pages to use the new Template:Concept_Listing==
We have created a Template:Concept_Listing that can be called in any location on any page where you want to create a table of links and summaries. (However, it does not allow you to change where the table is produced on API_Listing pages - see below.)

This decouples the Basic Listing Configuration section from the Template:API_Listing (which now serves only to provide the appropriate category, "API_Listings" to the page that uses it). This allows you to do landing pages that list and summarize all of the pages corresponding to the query you supply. See the Mobile Web landing page for an example.

Note, earlier in the thread we considered providing more than the two extant options for the table header, "Page" and "API Name" - and this is a good idea, we should pursue it - but we only had bandwidth to do as much as we did for now.

Also, the Form:API_Listing will continue to include the Template:Concept_Listing_Form_Section, which calls the Template:Concept_Listing at a specific location, so you can't put the Template:Concept_Listing anywhere you want in an API_Listing page. The PHP engine will just put it back under the Summary section when you edit the form. Here's the WebRTC API listing page for an example. If you are creating a new API_Listing page, you do it just like you used to - there is no change required in creating new API_Listing pages.

However, we will need to update the extant API_Listing pages to use this new method, because these pages are not yet calling the new Template:Concept_Listing_Form_Section with a query. Don't worry, though, the Template:API_Listing provides for legacy usage in API_Listing pages that still pass the query to it the old way, so there should be no wreckage in extant API_Listing pages. Once we have updated all the API_Listing pages, we'll remove the legacy usage.

To update an extant API_Listing page to use the new templates and forms:

# Navigate to an extant API_Listing page and '''Edit Source'''.
#  Under the '''<nowiki>{{API_Listing</nowiki>''' template call, copy the contents of the query into your buffer.
## Select everything after the '''Query=''' including the brackets; for example, '''<nowiki>[[Category:IndexedDB]][[Category:API_Objects]]</nowiki>'''.
## Press '''command c''' or '''Ctrl c''' or whatever.
# From the '''<nowiki>{{API_Listing</nowiki>''' call, delete the query entirely. That's the pipe character and everything up to but not including the closing '''}}'''.
#: For example, delete '''<nowiki>|Query=[[Category:IndexedDB]][[Category:API_Objects]]|Use_page_title=No|List_all_subpages=No</nowiki>''' so that the template call now reads simply, '''<nowiki>{{API_Listing}}</nowiki>'''
# Click '''Save page'''. Be sure the save takes - watch out for the old session data loss bug.
# '''Edit''' the page - this time with the form.
# Under '''Basic Listing Configuration''', in the '''Query''' field, paste the query from your buffer.
# Click '''Save page'''.
Your API_Listing is now using the new templates and forms appropriately.