These are early notes about the Flags concept.

==Design exploration==
===Presentation===
Most warning templates are displayed as a banner, often at the top of a page before the content, but sometimes inline in the content itself. This is eye-catching, but can be distracting.  The goal is to draw attention to the warning without detracting from the use of the page.

====Presentation Proposal====
One way to make is easy for people to assess the status easily is by having color-coded flags (e.g. CSS ribbons) with icon arranged along the top edge of the content area, each with a different indicator; mousing over these flags would raise a tooltip indicating the specific message.

(See [http://schepers.cc/wpd/Ribbons_Web_Elements_Preview2.jpg Top Ribbons] for a visual example of this type of flag, and [http://schepers.cc/webplatform/flags.svg Flags Mock] for a mock of what this could look like on this site.)

===User Experience===
Traditionally, these flags are added by using a specific bit of Mediawiki markdown to the page.  However, not everyone is familiar with the way to do this, and discovering the correct types of "content flags" is not obvious.

====UX Proposal====
Each page could feature a dropdown, with a Semantic Form backend, that automatically adds the appropriate flag template to the content (and also records who flagged it). This could look like a simple button that says "Flag this page", and expands into a set of options when pressed.

==Implementation==
You can see the current implementation of flags in the WPD wiki at the page [[css/properties/font-size]], and at its corresponding [http://webplatform.org/d/index.php?title=css/properties/font-size&action=formedit edit form].

The following are the pages involved in the data structure for setting flags:

"Form template" page (a reusable section of form syntax):
* [[Template:Flags form section]]

Display template (will eventually get called by each main template):
* [[Template:Flags‎]]

Property pages:
* [[Property:High-level issue]]
* [[Property:Content quality flag]]
* [[Property:Compatibility quality flag]]
* [[Property:Examples quality flag]]
* [[Property:Accessibility flag]]

And you can see one example of pages being aggregated by their flags, using a Semantic MediaWiki query, at [[Stub pages]].

==Requirements==
''This is a section kept for historical purposes only''
The specific implementation for this will require coordination between content needs, technical implementation abilities, and visual design. Here are the requirements that solutions should satisfy (in decreasing order of importance). Note that we're using "flags" as the catch-all term for these, but they might end up not being displayed that way.

* Allow flags to be displayed in different styles depending on which type they are. For example, some may show as little flags at the top of the content , some may be big banners at the top of the content, and others could be subtle and at the bottom of the content.
* Allow some method of listing which pages have a given flag on them
* Make it easy for editors to add or remove flags
* ''-- Big gap in priority--''
* Allow some tags to be related in behavior/style/meaning (e.g. subclassing or categories)
* Make it easy to define new tags as necessary ''(this will be pretty rare)''