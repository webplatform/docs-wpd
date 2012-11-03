{{TODO | Create a simple starter guide to bringing in compatibility table information here }}

==Overview==
"Compatibility Information" details which (CSS/HTML/JavaScript) features/APIs are supported by which browsers, as of which version.  Tables for this information are built into the templates for those elements, etc., and are automatically flagged as incomplete, which has them appear on a centralized list (http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace=).

The needed source information is available from the Mozilla Developer Network site (http://developer.mozilla.org), and the basic factual details can be freely copied (permission already given).  This information typically says when that support started (or ended), and so rarely changes.

We are generally most concerned initially with getting the newer features covered, so http://caniuse.com is another valuable reference.

{{Note | Extended prose discussions on compatibility may have citation and reuse issues, and so must be avoided (without training beyond this Getting Started guideline).  See http://docs.webplatform.org/wiki/WPD:External_Attribution.}}

Background -- this starter guide assumes that you are already registered with WPD and can edit wiki markup.  See http://docs.webplatform.org/wiki/WPD:Getting_Started.

==The basic process flow (to be detailed below)==
* locate and select an element that is missing Compatibility info
* check the item out for editing (tell others that you are working on it)
* look up the relevant info on mozdev
* extract the part that can be freely copied
* update the existing reference page with the Compatibility info
* check your work back in (note any gotchas, incompleteness, or issues, and let others know that your work is done and ready for review and/or use)

==Special instructions for the November Adobe Doc Sprint (or other doc sprints or hackathons)==
* avoiding collisions (simultaneous work on the same page by two contributors) and notifying others
* updating the task spreadsheet (google doc - https://docs.google.com/spreadsheet/ccc?key=0Aoc3F7WkVTNUdGg1UnVCakExMjZBUjIxYThGdTh5X2c#gid=0)

==Selecting items to update==
{{Note|We are most interested in covering the emerging and most recent features in JS/CSS3/HTML5.  If it was covered by Safari 1 or IE 4, the information is useful for completeness, but is not a priority.}}
* Use the official list (http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace=), and select a topic of interest.  As of Nov 2012 there are hundreds of items, so you may need to page forward for a while. (or)
* Pick something you already noticed was incomplete or missing.  Note that if the template doesn't include the Compatibility tables, you might want to double check that you are working on the most appropriate page.  Compatibility tables can be added manually, but that is beyond the scope of this Getting Started piece. (or)
* Browse the WPD site to locate a specific topic of interest (e.g., http://docs.webplatform.org/wiki/html/elements).

==Avoiding edit collisions==
Especially if you are engaged in a hackathon or doc sprint, we suggest that you establish a way to communicate across the group to avoid having two people taking the same element at the same time.  Similarly, avoid suggestions like "just take the first item on the list" (high probability of collision).
You can immediately start editing the page, going down to the Compatibility Information section, and clicking "Add Another" to add a bogus line item to the table, indicating you are currently editing -- put "editing by [your WPD user name] on [date]" as the "Area" (where the default is "Basic Support").  Save the changes as a minor edit, so that others can see that you are working on it.
{{Note|Be sure to click "Remove" to get rid of the bogus item when you are done.}}

==Locating the missing Compatibility Information==
You can login to the Mozilla Developer Network (http://developer.mozilla.org/) and search, or search Google (or your alternate) for MDN + (CSS | HTML | JS -- whichever area you're touching) + the element name.  For newer features (the ones we want you to start with) also check http://caniuse.com.

For MDN, you can use the basic facts (version numbers, yes/no on support) without attribution.  WPD has already made this arrangement.  For all others, you should follow the attribution guidelines ().

Examples:
* GetElementById
* Blur
*