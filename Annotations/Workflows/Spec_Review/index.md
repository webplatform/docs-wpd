---
title: WPD:Annotations/Workflows/Spec Review
---
<p>In order to comment on a specification at W3C, a new community member faces significant hurdles. In addition, a Working Group is not well-equipped by our current toolchain to record, resolve, and demonstrate response to feedback.
</p>
<h2><span class="mw-headline" id="Current_Workflow">Current Workflow</span></h2>
<h3><span class="mw-headline" id="Review">Review</span></h3>
<ol><li> Reviewer reads spec, finds portion that requires comment</li>
<li> Reviewer seeks proper feedback channel
<ol><li> Not obvious which group to provide feedback to </li>
<li> Not obvious that the feedback channel is email</li>
<li> In most specs, not obvious where the email address is located; usually buried in boilerplate in "Status of this Document" section, without metadata or styling to set it apart from other boilerplate</li>
<li> <i>Note that many designers do not like email as a mode of communication</i></li></ol></li>
<li> Reviewer subscribes to email list
<ol><li> Reviewer must notice and reply to Archive Authorization email after sending first email, or that email will not go through (this can be confusing and frustrating)</li>
<li> Reviewer receives all emails sent to list, not only those relevant to their topic of interest</li></ol></li>
<li> Reviewer optionally copies link to section of spec, pastes in email</li>
<li> Reviewer optionally copies text in question, pastes in email</li>
<li> Reviewer preferably prefaces subject line with "code" for the particular spec (e.g. [composting-1]), as instructed in spec</li>
<li> Reviewer writes comment, hopefully contextualizing adequately</li>
<li> Reviewer waits for response from WG</li></ol>
<p><i>Note that to overcome the overhead of commenting, reviewers often compile several issues into a single email, which is harder for WGs to process and track.</i>
</p><p><i>Note that some WGs request for reviewers to create their own issues in the issue tracker, which is more convenient for WG, but also has several steps for the reviewer.</i>
</p>
<h3><span class="mw-headline" id="Working_Group">Working Group</span></h3>
<ol><li> WG must notice email</li>
<li> WG adds email to discussion
<ol><li> Adds topic to agenda</li>
<li> Requests clarification on any confusing parts</li></ol></li>
<li> WG contextualizes comment by corresponding it to the proper section of the spec, which is often difficult</li>
<li> WG discusses issue (on weekly basis), decides disposition
<ol><li> WG categorizes nature of comment (e.g. editorial, normative, substantive, etc.)</li></ol></li>
<li> WG assigns action to WG member
<ol><li> WG member adds email to issue tracker
<ol><li> Creates new issue</li>
<li> Copies and pastes archive link into issue</li>
<li> Copies relevant parts of email into issue</li>
<li> Optionally adds issue id to email for tracking responses</li></ol></li>
<li> WG member responds to reviewer </li>
<li> WG member changes spec, if necessary</li></ol></li></ol>
<p><i>Note that the average time to response, or especially to resolution, is often discouraging to reviewers.</i>
</p><p><i>Note that it takes discipline for a WG to consistently add issues to the issue tracker, and emails often slip through the cracks, even when they are added as issues.</i>
</p>
<h3><span class="mw-headline" id="Transition">Transition</span></h3>
<ol><li> WG creates <a rel="nofollow" class="external text" href="http://www.w3.org/Graphics/SVG/1.2/Tiny/dc.html">Disposition of Comments</a>
<ol><li> Disposition of Comments should include link to original review, trail of responses, resolution by WG, and satisfaction of reviewer</li>
<li> Disposition of Comments does not contextualize comment in spec, or show actual changes made</li>
<li> Disposition of Comments can be time-consuming to create, and is prone to unintentional omissions</li></ol></li>
<li> Director reviews Disposition of Comments</li>
<li> Director asks WG (staff contact, chairs) specific questions about Disposition of Comments
<ol><li> Details of specification changes and context of changes is often not drilled into</li></ol></li>
<li> Director makes decision on document transition status, sometimes with caveats </li></ol>
<h2><span class="mw-headline" id="Possible_Workflow_with_Annotations">Possible Workflow with Annotations</span></h2>
<h3><span class="mw-headline" id="Review_2">Review</span></h3>
<ol><li> Reviewer reads spec, finds portion that requires comment</li>
<li> Reviewer creates account (on WebPlatform.org, in current plan)
<ol><li> Reviewer agrees to archive authorization as part of account creation process</li>
<li> Reviewer signs in</li></ol></li>
<li> Reviewer highlights passage to comment on</li>
<li> Reviewer writes comment, automatically contextualized in spec</li>
<li> Reviewer tags comment with category (e.g. editorial, normative, substantive, etc.)</li>
<li> Email is automatically sent to the correct mailing list
<ol><li> Email has headers for spec, tags, and reply-to </li></ol></li>
<li> Reviewer waits for response from WG</li></ol>
<h3><span class="mw-headline" id="Working_Group_2">Working Group</span></h3>
<ol><li> WG notified by email that comment has been made on a specific spec
<ol><li> Spec editor more likely to notice comments on their own spec, less likely to miss comments not given special subject line, easier to sort and filter</li></ol></li>
<li> WG adds comment to discussion
<ol><li> Adds topic to agenda</li>
<li> Requests clarification on any confusing parts, sometimes in real-time via threaded comment interface</li></ol></li>
<li> WG discusses issue (on weekly basis), decides disposition</li>
<li> WG assigns action to WG member
<ol><li> Comment already tracked via annotation, with full context</li>
<li> WG member responds to reviewer 
<ol><li> Responses to reviewer carry thread and tag headers in email, for ease of tracking</li></ol></li>
<li> WG member changes spec, if necessary
<ol><li> Optionally in future, annotation system could allow editor / change-controller to automatically accept proposed changes by commenter, replacing the text in the spec via bot</li></ol></li>
<li> WG member changes status of annotation comment</li></ol></li></ol>
<h3><span class="mw-headline" id="Transition_2">Transition</span></h3>
<ol><li> WG creates <a rel="nofollow" class="external text" href="http://www.w3.org/Graphics/SVG/1.2/Tiny/dc.html">Disposition of Comments</a>
<ol><li> Disposition of Comments automatically include link to original comment, trail of responses, resolution by WG, and satisfaction of reviewer, for comments submitted by annotation system
<ol><li> For comments submitted by email, WG can add them, contextualized in spec, manually</li></ol></li>
<li> Disposition of Comments would contextualize comment in spec, and would highlight actual changes made</li>
<li> Disposition of Comments would be generated automatically, less prone to unintentional omissions</li></ol></li>
<li> Director reviews Disposition of Comments, in context of spec</li>
<li> Director asks WG (staff contact, chairs) specific questions about Disposition of Comments, can easily follow threaded conversations
<ol><li> Details of specification changes and context of changes more easily not drilled into</li></ol></li>
<li> Director makes decision on document transition status, sometimes with caveats</li></ol>

<!-- 
NewPP limit report
CPU time usage: 0.018 seconds
Real time usage: 0.019 seconds
Preprocessor visited node count: 31/1000000
Preprocessor generated node count: 36/1000000
Post‐expand include size: 0/2097152 bytes
Template argument size: 0/2097152 bytes
Highest expansion depth: 2/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%    0.000      1 - -total
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:13391-0!*!*!!*!*!*!esi=1 and timestamp 20150731012639 and revision id 42844
 -->
