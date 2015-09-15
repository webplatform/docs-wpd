---
title: Spec Review
uri: 'WPD:Annotations/Workflows/Spec Review'

---
In order to comment on a specification at W3C, a new community member faces significant hurdles. In addition, a Working Group is not well-equipped by our current toolchain to record, resolve, and demonstrate response to feedback.

## <span>Current Workflow</span>

### <span>Review</span>

1.  Reviewer reads spec, finds portion that requires comment
2.  Reviewer seeks proper feedback channel
    1.  Not obvious which group to provide feedback to
    2.  Not obvious that the feedback channel is email
    3.  In most specs, not obvious where the email address is located; usually buried in boilerplate in "Status of this Document" section, without metadata or styling to set it apart from other boilerplate
    4.  *Note that many designers do not like email as a mode of communication*

3.  Reviewer subscribes to email list
    1.  Reviewer must notice and reply to Archive Authorization email after sending first email, or that email will not go through (this can be confusing and frustrating)
    2.  Reviewer receives all emails sent to list, not only those relevant to their topic of interest

4.  Reviewer optionally copies link to section of spec, pastes in email
5.  Reviewer optionally copies text in question, pastes in email
6.  Reviewer preferably prefaces subject line with "code" for the particular spec (e.g. [composting-1]), as instructed in spec
7.  Reviewer writes comment, hopefully contextualizing adequately
8.  Reviewer waits for response from WG

*Note that to overcome the overhead of commenting, reviewers often compile several issues into a single email, which is harder for WGs to process and track.*

*Note that some WGs request for reviewers to create their own issues in the issue tracker, which is more convenient for WG, but also has several steps for the reviewer.*

### <span>Working Group</span>

1.  WG must notice email
2.  WG adds email to discussion
    1.  Adds topic to agenda
    2.  Requests clarification on any confusing parts

3.  WG contextualizes comment by corresponding it to the proper section of the spec, which is often difficult
4.  WG discusses issue (on weekly basis), decides disposition
    1.  WG categorizes nature of comment (e.g. editorial, normative, substantive, etc.)

5.  WG assigns action to WG member
    1.  WG member adds email to issue tracker
        1.  Creates new issue
        2.  Copies and pastes archive link into issue
        3.  Copies relevant parts of email into issue
        4.  Optionally adds issue id to email for tracking responses

    2.  WG member responds to reviewer
    3.  WG member changes spec, if necessary

*Note that the average time to response, or especially to resolution, is often discouraging to reviewers.*

*Note that it takes discipline for a WG to consistently add issues to the issue tracker, and emails often slip through the cracks, even when they are added as issues.*

### <span>Transition</span>

1.  WG creates [Disposition of Comments](http://www.w3.org/Graphics/SVG/1.2/Tiny/dc.html)
    1.  Disposition of Comments should include link to original review, trail of responses, resolution by WG, and satisfaction of reviewer
    2.  Disposition of Comments does not contextualize comment in spec, or show actual changes made
    3.  Disposition of Comments can be time-consuming to create, and is prone to unintentional omissions

2.  Director reviews Disposition of Comments
3.  Director asks WG (staff contact, chairs) specific questions about Disposition of Comments
    1.  Details of specification changes and context of changes is often not drilled into

4.  Director makes decision on document transition status, sometimes with caveats

## <span>Possible Workflow with Annotations</span>

### <span>Review</span>

1.  Reviewer reads spec, finds portion that requires comment
2.  Reviewer creates account (on WebPlatform.org, in current plan)
    1.  Reviewer agrees to archive authorization as part of account creation process
    2.  Reviewer signs in

3.  Reviewer highlights passage to comment on
4.  Reviewer writes comment, automatically contextualized in spec
5.  Reviewer tags comment with category (e.g. editorial, normative, substantive, etc.)
6.  Email is automatically sent to the correct mailing list
    1.  Email has headers for spec, tags, and reply-to

7.  Reviewer waits for response from WG

### <span>Working Group</span>

1.  WG notified by email that comment has been made on a specific spec
    1.  Spec editor more likely to notice comments on their own spec, less likely to miss comments not given special subject line, easier to sort and filter

2.  WG adds comment to discussion
    1.  Adds topic to agenda
    2.  Requests clarification on any confusing parts, sometimes in real-time via threaded comment interface

3.  WG discusses issue (on weekly basis), decides disposition
4.  WG assigns action to WG member
    1.  Comment already tracked via annotation, with full context
    2.  WG member responds to reviewer
        1.  Responses to reviewer carry thread and tag headers in email, for ease of tracking

    3.  WG member changes spec, if necessary
        1.  Optionally in future, annotation system could allow editor / change-controller to automatically accept proposed changes by commenter, replacing the text in the spec via bot

    4.  WG member changes status of annotation comment

### <span>Transition</span>

1.  WG creates [Disposition of Comments](http://www.w3.org/Graphics/SVG/1.2/Tiny/dc.html)
    1.  Disposition of Comments automatically include link to original comment, trail of responses, resolution by WG, and satisfaction of reviewer, for comments submitted by annotation system
        1.  For comments submitted by email, WG can add them, contextualized in spec, manually

    2.  Disposition of Comments would contextualize comment in spec, and would highlight actual changes made
    3.  Disposition of Comments would be generated automatically, less prone to unintentional omissions

2.  Director reviews Disposition of Comments, in context of spec
3.  Director asks WG (staff contact, chairs) specific questions about Disposition of Comments, can easily follow threaded conversations
    1.  Details of specification changes and context of changes more easily not drilled into

4.  Director makes decision on document transition status, sometimes with caveats
