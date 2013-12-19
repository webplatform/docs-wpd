In order to comment on a specification at W3C, a new community member faces significant hurdles. In addition, a Working Group is not well-equipped by our current toolchain to record, resolve, and demonstrate response to feedback.

==Current Workflow==
===Review===
# Reviewer reads spec, finds portion that requires comment
# Reviewer seeks proper feedback channel
## Not obvious which group to provide feedback to 
## Not obvious that the feedback channel is email
## In most specs, not obvious where the email address is located; usually buried in boilerplate in "Status of this Document" section, without metadata or styling to set it apart from other boilerplate
## ''Note that many designers do not like email as a mode of communication''
# Reviewer subscribes to email list
## Reviewer must notice and reply to Archive Authorization email after sending first email, or that email will not go through (this can be confusing and frustrating)
## Reviewer receives all emails sent to list, not only those relevant to their topic of interest
# Reviewer optionally copies link to section of spec, pastes in email
# Reviewer optionally copies text in question, pastes in email
# Reviewer preferably prefaces subject line with "code" for the particular spec (e.g. [composting-1]), as instructed in spec
# Reviewer writes comment, hopefully contextualizing adequately
# Reviewer waits for response from WG

''Note that to overcome the overhead of commenting, reviewers often compile several issues into a single email, which is harder for WGs to process and track.''

''Note that some WGs request for reviewers to create their own issues in the issue tracker, which is more convenient for WG, but also has several steps for the reviewer.''

===Working Group===
# WG must notice email
# WG adds email to discussion
## Adds topic to agenda
## Requests clarification on any confusing parts
# WG contextualizes comment by corresponding it to the proper section of the spec, which is often difficult
# WG discusses issue (on weekly basis), decides disposition
## WG categorizes nature of comment (e.g. editorial, normative, substantive, etc.)
# WG assigns action to WG member
## WG member adds email to issue tracker
### Creates new issue
### Copies and pastes archive link into issue
### Copies relevant parts of email into issue
### Optionally adds issue id to email for tracking responses
## WG member responds to reviewer 
## WG member changes spec, if necessary

''Note that the average time to response, or especially to resolution, is often discouraging to reviewers.''

''Note that it takes discipline for a WG to consistently add issues to the issue tracker, and emails often slip through the cracks, even when they are added as issues.''

===Transition===
# WG creates [http://www.w3.org/Graphics/SVG/1.2/Tiny/dc.html Disposition of Comments]
## Disposition of Comments should include link to original review, trail of responses, resolution by WG, and satisfaction of reviewer
## Disposition of Comments does not contextualize comment in spec, or show actual changes made
## Disposition of Comments can be time-consuming to create, and is prone to unintentional omissions
# Director reviews Disposition of Comments
# Director asks WG (staff contact, chairs) specific questions about Disposition of Comments
## Details of specification changes and context of changes is often not drilled into
# Director makes decision on document transition status, sometimes with caveats 

==Possible Workflow with Annotations==
===Review===
# Reviewer reads spec, finds portion that requires comment
# Reviewer creates account (on WebPlatform.org, in current plan)
## Reviewer agrees to archive authorization as part of account creation process
## Reviewer signs in
# Reviewer highlights passage to comment on
# Reviewer writes comment, automatically contextualized in spec
# Reviewer tags comment with category (e.g. editorial, normative, substantive, etc.)
# Email is automatically sent to the correct mailing list
## Email has headers for spec, tags, and reply-to 
# Reviewer waits for response from WG

===Working Group===
# WG notified by email that comment has been made on a specific spec
## Spec editor more likely to notice comments on their own spec, less likely to miss comments not given special subject line, easier to sort and filter
# WG adds comment to discussion
## Adds topic to agenda
## Requests clarification on any confusing parts, sometimes in real-time via threaded comment interface
# WG discusses issue (on weekly basis), decides disposition
# WG assigns action to WG member
## Comment already tracked via annotation, with full context
## WG member responds to reviewer 
### Responses to reviewer carry thread and tag headers in email, for ease of tracking
## WG member changes spec, if necessary
### Optionally in future, annotation system could allow editor / change-controller to automatically accept proposed changes by commenter, replacing the text in the spec via bot
## WG member changes status of annotation comment

===Transition===
# WG creates [http://www.w3.org/Graphics/SVG/1.2/Tiny/dc.html Disposition of Comments]
## Disposition of Comments automatically include link to original comment, trail of responses, resolution by WG, and satisfaction of reviewer, for comments submitted by annotation system
### For comments submitted by email, WG can add them, contextualized in spec, manually
## Disposition of Comments would contextualize comment in spec, and would highlight actual changes made
## Disposition of Comments would be generated automatically, less prone to unintentional omissions
# Director reviews Disposition of Comments, in context of spec
# Director asks WG (staff contact, chairs) specific questions about Disposition of Comments, can easily follow threaded conversations
## Details of specification changes and context of changes more easily not drilled into
# Director makes decision on document transition status, sometimes with caveats