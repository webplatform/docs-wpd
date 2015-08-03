---
title: WPD:Getting Started/Compatibility
---
<h2><span class="mw-headline" id="Overview">Overview</span></h2>
<p>The "Compatibility Information" tables detail which (CSS/HTML/JavaScript) features/APIs are supported by which browsers, as of which version.  Tables for this information are built into the templates for those elements, etc., presented under "Browser Compatibility" (with separate tabs for desktop and mobile), and are automatically flagged as incomplete, which has them appear on a <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&amp;target=Template%3ACompat+Unknown&amp;namespace=">centralized list</a>.
</p><p>The needed source information is available from the <a rel="nofollow" class="external text" href="http://developer.mozilla.org">Mozilla Developer Network site</a>, and the basic factual details can be freely copied (permission already given).  This information typically indicates when (as of which browser version) that support started (or ended), and so these details rarely change.
</p><p>We are generally most concerned initially with getting the newer features covered, so <a rel="nofollow" class="external free" href="http://caniuse.com">http://caniuse.com</a> is another valuable reference.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>:  Extended prose discussions on compatibility may have citation and reuse issues, and so must be avoided (without training beyond this Getting Started guideline).  See the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:External_Attribution">attribution guidelines</a>.
</p>
</div>
<p><br />
Background -- this starter guide assumes that you are already registered with WPD and can edit wiki markup.  See the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:Getting_Started">main getting started guidelines</a>.
</p>
<h2><span class="mw-headline" id="The_basic_process_flow_.28detailed_below.29">The basic process flow (detailed below)</span></h2>
<ul><li> locate and select an element that is missing Compatibility info</li>
<li> check the item out for editing (tell others that you are working on it)</li>
<li> look up the relevant info on mozdev or elsewhere</li>
<li> extract the part that can be freely copied</li>
<li> update the existing reference page with the Compatibility info</li>
<li> check your work back in (note any gotchas, incompleteness, or issues, and let others know that your work is done and ready for review and/or use)</li></ul>
<h2><span class="mw-headline" id="Special_instructions_for_the_November_2012_Adobe_Doc_Sprint_.28or_other_doc_sprints_or_hackathons.29">Special instructions for the November 2012 Adobe Doc Sprint (or other doc sprints or hackathons)</span></h2>
<p>These instructions were created in order to set up the Compatibility Info update as a quick entry point for new participants to engage.  In order to have everyone's efforts make a difference, some special attention is needed.
</p>
<ul><li> Avoiding collisions (simultaneous work on the same page by two contributors) and notifying others -- see "Avoiding edit collisions" (below).</li></ul>
<ul><li> Updating the task spreadsheet (the google doc for the Nov 2012 event at Adobe SF is/was <a rel="nofollow" class="external text" href="https://docs.google.com/spreadsheet/ccc?key=0Aoc3F7WkVTNUdGg1UnVCakExMjZBUjIxYThGdTh5X2c#gid=0">here</a>)</li></ul>
<p>With hundreds of incomplete compatibility items flagged in WPD, there is currently only a generic task item in the tracking spreadsheet.  You can clone/copy the row and show it as "In process" with your WPD userid, and put the topics you have done or are working on in the "Notes" field.  If you do a single item (as your "warm-up" exercise), you can then flag it complete and move on to your next task.  If you are going to do a bunch, try to locate the others who are doing the same and work out a way to keep up the momentum without colliding.
</p><p>One suggestion for event organizers might be to pull a list of prioritized topics to hit, and then let participants pull from the list, or have others nominate priority topics (the official report from the repo can a bit daunting, at this stage).
</p>
<div style="border:1px solid hsl(45, 100%, 40%); padding:5px; margin:5px; background-color:hsl(45, 88%, 94%); border-radius:5px">
<p><b>TODO</b>:  Consider splitting this into a basics training for new users, and a quick reference just for Compatibility Info. 
</p>
</div>
<h2><span class="mw-headline" id="Selecting_items_to_update">Selecting items to update</span></h2>
<div class="note">
<p><b>Note</b>: We are most interested in covering the emerging and most recent features in JS/CSS3/HTML5.  If it was covered by Safari 1 or IE 4, the information is useful for completeness, but is not a priority.
</p>
</div>
<ul><li> Use the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/index.php?title=Special%3AWhatLinksHere&amp;target=Template%3ACompat+Unknown&amp;namespace=">official list</a>, and select a topic of interest.  As of Nov 2012 there are hundreds of items, so you may need to page forward for a while. (or)</li>
<li> Pick something you already noticed was incomplete or missing.  Note that if the template doesn't include the Compatibility tables, you might want to double check that you are working on the most appropriate page.  Compatibility tables can be added manually, but that is beyond the scope of this Getting Started piece. (or)</li>
<li> Browse the WPD site to locate a specific topic of interest (e.g., <a rel="nofollow" class="external free" href="http://docs.webplatform.org/wiki/html/elements">http://docs.webplatform.org/wiki/html/elements</a>).</li></ul>
<h2><span class="mw-headline" id="Avoiding_edit_collisions">Avoiding edit collisions</span></h2>
<p>Especially if you are engaged in a hackathon or doc sprint, we suggest that you establish a way to communicate across the group(s) to avoid having two people taking the same element at the same time.  Similarly, avoid suggestions like "just take the first item on the list" (high probability of collision).  This can be done verbally, electronically, or using a flipchart or white board.
</p><p>Even outside a large-group setting, you can take steps to protect the value of your contribution -- you can immediately start editing the page, going down to the Compatibility Information section, and clicking "Add Another" to add a bogus line item to the table, indicating you are currently editing -- put "editing by [your WPD user name] on [date]" as the "Area" (where the default is "Basic Support").  Save the changes as a minor edit, so that others can see that you are working on it.  
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>: Be sure to click "Remove" to get rid of the bogus item when you are done.
</p>
</div>
<p><br />
Look for such a row before you start researching missing info.
</p>
<h2><span class="mw-headline" id="Locating_the_missing_Compatibility_Information">Locating the missing Compatibility Information</span></h2>
<p>You can login to the Mozilla Developer Network (<a rel="nofollow" class="external free" href="http://developer.mozilla.org/">http://developer.mozilla.org/</a>) and search, or search Google (or your alternate) for MDN + (CSS | HTML | JS -- whichever area you're touching) + the element name.  For newer features (the ones we want you to start with) also check <a rel="nofollow" class="external free" href="http://caniuse.com">http://caniuse.com</a>.
</p><p>For each item, you want to note which browser version was the first to provide complete support.  If only partial support is currently provided, note that with "(partial)" after the version number.
</p><p>For MDN, you can use the basic facts (version numbers, yes/no/partial on support) without attribution.  WPD has already made this arrangement.  For all others, you should follow the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/wiki/WPD:External_Attribution">attribution guidelines</a>.
</p>
<h2><span class="mw-headline" id="Compatibility_details">Compatibility details</span></h2>
<p>Note that especially the new, emergent, proposed, and transitional features tend to be implemented in browser-specific ways.  This is usually done with a browser-specific prefix on the tag (e.g., -moz- or -ms-).  There are two rows in the Compatibility Table templates for each browser, to cover both the common standards and the vendor-specific (prefixed) versions.
</p><p>There are separate tables for Desktop and for Mobile support.  One may be filled in while the other is still incomplete (driven by the editor's focus).
</p><p>Each element is either supported or not (radio buttons for yes, no, and unknown).  If it is supported, there is a minimum browser version that supports it (and presumably all higher versions will also support it).
</p><p>For some elements, there may be sub-elements or features that need to called out individually.  For these, after you have covered the Basic Support, you can click the "Add Another" button to add rows to the table.
</p><p>Examples of multi-row Compatibility tables are:
</p>
<ul><li> the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/w/index.php?title=html/elements/audio">audio tag</a> which has separate rows for the various codecs covered in the HTML5 spec, since support differs significantly across vendors</li>
<li> [get something with sub-elements]</li></ul>
<p>Additional rows should be sorted by name.  Use the drag handles to the right of the "Remove" button to move an item up or down in the list.
</p>
<h2><span class="mw-headline" id="Compatibility_Notes">Compatibility Notes</span></h2>
<p>There is a third table in the compatibility section for Compatibility Notes.  Use this to cover anything that can't be covered just by yes/no/?? and a version number.  Just click "Add another" to insert a row.
</p>
<h2><span class="mw-headline" id="Save_your_work">Save your work</span></h2>
<p>When you have completed your edits (or have simply done a significant piece of work which is not yet saved), enter a summary of your changes (if needed), check the box for a "minor edit" if you only tweaked existing info, click "Show preview" to review your work (recommended), and then click "Save page" to finish.
</p><p><br />
</p>
<div class="note">
<p><b>Note</b>: If you have been editing for a while without saving, your session info might be stale, and <i>your work will not be saved.</i>  You can tell because you get a warning message starting with "Sorry! We could not process your edit due to a loss of session data. Please try again...." (along with a deceptively updated preview of your unprocessed new version, and the edited source).  Most of the time, just resubmitting will work fine (the first attempt refreshes your session, so the second attempt goes through).
</p>
</div>
<p><br />
</p>
<h2><span class="mw-headline" id="Closure_and_exceptions">Closure and exceptions</span></h2>
<p>If you feel that the Compatibility Info is now complete (for both desktop and mobile browsers), you can uncheck the "Compatibility Incomplete" box in the Content section just below the page title (the checkbox is to the left of the text, at least in the English version).  
</p><p>If you feel that no compatibility information is needed for this topic (it was on the list because it was checked by default), you can check the box immediately under the "Compatibility" section header, which indicates that this section is not needed (and so will not appear).  Be sure to uncheck the "Compatibility Incomplete" box near the top of the page, too, if needed.
</p><p>Your final summary (commit) comment should mention if you have changed the status, and you should be sure to mention any outstanding issues, items or questions, possibly with a {{TODO | [here is what is still missing, or where to look] }} tag somewhere on the page.
</p><p>Finally, remove any "edit in progress" rows you might have added, and update your global team if you are coordinating within a large event.
</p><p>Congratulate yourself, and thanks for contributing!
</p>
<!-- 
NewPP limit report
CPU time usage: 0.040 seconds
Real time usage: 0.045 seconds
Preprocessor visited node count: 80/1000000
Preprocessor generated node count: 191/1000000
Post‐expand include size: 1459/2097152 bytes
Template argument size: 1146/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   12.390      1 - -total
 62.67%    7.764      4 - Template:Note
 23.95%    2.967      1 - Template:TODO
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6321-0!*!*!!*!*!*!esi=1 and timestamp 20150730201458 and revision id 16622
 -->
