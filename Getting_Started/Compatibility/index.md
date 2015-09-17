---
title: 'Compatibility'
uri: 'WPD:Getting Started/Compatibility'

---
## Overview

The "Compatibility Information" tables detail which (CSS/HTML/JavaScript) features/APIs are supported by which browsers, as of which version. Tables for this information are built into the templates for those elements, etc., presented under "Browser Compatibility" (with separate tabs for desktop and mobile), and are automatically flagged as incomplete, which has them appear on a [centralized list](http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace=).

The needed source information is available from the [Mozilla Developer Network site](http://developer.mozilla.org), and the basic factual details can be freely copied (permission already given). This information typically indicates when (as of which browser version) that support started (or ended), and so these details rarely change.

We are generally most concerned initially with getting the newer features covered, so <http://caniuse.com> is another valuable reference.

**Note**: Extended prose discussions on compatibility may have citation and reuse issues, and so must be avoided (without training beyond this Getting Started guideline). See the [attribution guidelines](http://docs.webplatform.org/wiki/WPD:External_Attribution).

 Background -- this starter guide assumes that you are already registered with WPD and can edit wiki markup. See the [main getting started guidelines](http://docs.webplatform.org/wiki/WPD:Getting_Started).

## The basic process flow (detailed below)

-   locate and select an element that is missing Compatibility info
-   check the item out for editing (tell others that you are working on it)
-   look up the relevant info on mozdev or elsewhere
-   extract the part that can be freely copied
-   update the existing reference page with the Compatibility info
-   check your work back in (note any gotchas, incompleteness, or issues, and let others know that your work is done and ready for review and/or use)

## Special instructions for the November 2012 Adobe Doc Sprint (or other doc sprints or hackathons)

These instructions were created in order to set up the Compatibility Info update as a quick entry point for new participants to engage. In order to have everyone's efforts make a difference, some special attention is needed.

-   Avoiding collisions (simultaneous work on the same page by two contributors) and notifying others -- see "Avoiding edit collisions" (below).

-   Updating the task spreadsheet (the google doc for the Nov 2012 event at Adobe SF is/was [here](https://docs.google.com/spreadsheet/ccc?key=0Aoc3F7WkVTNUdGg1UnVCakExMjZBUjIxYThGdTh5X2c#gid=0))

With hundreds of incomplete compatibility items flagged in WPD, there is currently only a generic task item in the tracking spreadsheet. You can clone/copy the row and show it as "In process" with your WPD userid, and put the topics you have done or are working on in the "Notes" field. If you do a single item (as your "warm-up" exercise), you can then flag it complete and move on to your next task. If you are going to do a bunch, try to locate the others who are doing the same and work out a way to keep up the momentum without colliding.

One suggestion for event organizers might be to pull a list of prioritized topics to hit, and then let participants pull from the list, or have others nominate priority topics (the official report from the repo can a bit daunting, at this stage).

**TODO**: Consider splitting this into a basics training for new users, and a quick reference just for Compatibility Info.

## Selecting items to update

**Note**: We are most interested in covering the emerging and most recent features in JS/CSS3/HTML5. If it was covered by Safari 1 or IE 4, the information is useful for completeness, but is not a priority.

-   Use the [official list](http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&target=Template%3ACompat+Unknown&namespace=), and select a topic of interest. As of Nov 2012 there are hundreds of items, so you may need to page forward for a while. (or)
-   Pick something you already noticed was incomplete or missing. Note that if the template doesn't include the Compatibility tables, you might want to double check that you are working on the most appropriate page. Compatibility tables can be added manually, but that is beyond the scope of this Getting Started piece. (or)
-   Browse the WPD site to locate a specific topic of interest (e.g., <http://docs.webplatform.org/wiki/html/elements>).

## Avoiding edit collisions

Especially if you are engaged in a hackathon or doc sprint, we suggest that you establish a way to communicate across the group(s) to avoid having two people taking the same element at the same time. Similarly, avoid suggestions like "just take the first item on the list" (high probability of collision). This can be done verbally, electronically, or using a flipchart or white board.

Even outside a large-group setting, you can take steps to protect the value of your contribution -- you can immediately start editing the page, going down to the Compatibility Information section, and clicking "Add Another" to add a bogus line item to the table, indicating you are currently editing -- put "editing by [your WPD user name] on [date]" as the "Area" (where the default is "Basic Support"). Save the changes as a minor edit, so that others can see that you are working on it.

**Note**: Be sure to click "Remove" to get rid of the bogus item when you are done.

 Look for such a row before you start researching missing info.

## Locating the missing Compatibility Information

You can login to the Mozilla Developer Network (<http://developer.mozilla.org/>) and search, or search Google (or your alternate) for MDN + (CSS | HTML | JS -- whichever area you're touching) + the element name. For newer features (the ones we want you to start with) also check <http://caniuse.com>.

For each item, you want to note which browser version was the first to provide complete support. If only partial support is currently provided, note that with "(partial)" after the version number.

For MDN, you can use the basic facts (version numbers, yes/no/partial on support) without attribution. WPD has already made this arrangement. For all others, you should follow the [attribution guidelines](http://docs.webplatform.org/wiki/WPD:External_Attribution).

## Compatibility details

Note that especially the new, emergent, proposed, and transitional features tend to be implemented in browser-specific ways. This is usually done with a browser-specific prefix on the tag (e.g., -moz- or -ms-). There are two rows in the Compatibility Table templates for each browser, to cover both the common standards and the vendor-specific (prefixed) versions.

There are separate tables for Desktop and for Mobile support. One may be filled in while the other is still incomplete (driven by the editor's focus).

Each element is either supported or not (radio buttons for yes, no, and unknown). If it is supported, there is a minimum browser version that supports it (and presumably all higher versions will also support it).

For some elements, there may be sub-elements or features that need to called out individually. For these, after you have covered the Basic Support, you can click the "Add Another" button to add rows to the table.

Examples of multi-row Compatibility tables are:

-   the [audio tag](http://docs.webplatform.org/w/index.php?title=html/elements/audio) which has separate rows for the various codecs covered in the HTML5 spec, since support differs significantly across vendors
-   [get something with sub-elements]

Additional rows should be sorted by name. Use the drag handles to the right of the "Remove" button to move an item up or down in the list.

## Compatibility Notes

There is a third table in the compatibility section for Compatibility Notes. Use this to cover anything that can't be covered just by yes/no/?? and a version number. Just click "Add another" to insert a row.

## Save your work

When you have completed your edits (or have simply done a significant piece of work which is not yet saved), enter a summary of your changes (if needed), check the box for a "minor edit" if you only tweaked existing info, click "Show preview" to review your work (recommended), and then click "Save page" to finish.

**Note**: If you have been editing for a while without saving, your session info might be stale, and *your work will not be saved.* You can tell because you get a warning message starting with "Sorry! We could not process your edit due to a loss of session data. Please try again...." (along with a deceptively updated preview of your unprocessed new version, and the edited source). Most of the time, just resubmitting will work fine (the first attempt refreshes your session, so the second attempt goes through).

## Closure and exceptions

If you feel that the Compatibility Info is now complete (for both desktop and mobile browsers), you can uncheck the "Compatibility Incomplete" box in the Content section just below the page title (the checkbox is to the left of the text, at least in the English version).

If you feel that no compatibility information is needed for this topic (it was on the list because it was checked by default), you can check the box immediately under the "Compatibility" section header, which indicates that this section is not needed (and so will not appear). Be sure to uncheck the "Compatibility Incomplete" box near the top of the page, too, if needed.

Your final summary (commit) comment should mention if you have changed the status, and you should be sure to mention any outstanding issues, items or questions, possibly with a {{TODO | [here is what is still missing, or where to look] }} tag somewhere on the page.

Finally, remove any "edit in progress" rows you might have added, and update your global team if you are coordinating within a large event.

Congratulate yourself, and thanks for contributing!
