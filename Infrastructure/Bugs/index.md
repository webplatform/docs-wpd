{{Flags}}
{{Basic Page}}
==Introduction==

Webplatform.org uses the [https://www.w3.org/Bugs/Public/ W3C's public bug], project and issue Tracking Service, using the open-source [http://www.bugzilla.org/ bugzilla] platform. We use this tool for bugs about infrastructure problems, administrative issues, and the like. Problems about the content and that are found in the topics within the WPD content library should be flagged in the topic and fixed by and within the community. 

While the W3C maintains a [https://www.w3.org/Bugs/Public/page.cgi?id=quicksearch.html page with help topics], this page is a rudimentary getting started.

==Categorizing bugs==

You can begin a search for any bugs from [https://www.w3.org/Bugs/Public/query.cgi https://www.w3.org/Bugs/Public/query.cgi]. You can toggle between simple and advanced search by using the tabs on the page. The simple search will scour a product for strings, and the advanced search has pretty powerful capability pivoting on a number of factors. Note that the built-in functionality via the links at the bottom of the page vary depending on whether you're using simple or advanced search.


==Database Fields==

Bugzilla uses the following criteria for categorizing bugs. Use the product in the simple search and the product along with the other fields when searching for bugs in the advanced search. You can search on fields such as URL, comment, keywords, and more. 

{|
! Field
! Value
! Mandatory?
|-
| Component
| ''default'' (the only one we have right now)
| Yes
|-
| Version
| ''unspecified''
| 
|-
| Target Milestone
| TBD
| 
|-
| Severity
| ranges from ''enhancement'' to ''blocker''
| 
|-
| Hardware
| Types of hardware in dropdown
| 
|-
| Priority
| P1 to P5. Default is P2.
| 
|-
| Initial State
| This describes the bug. Default is ''New''
| 
|-
| Assign To
| email address of the registered DB user. Default is dave.null@w3.org.
| 
|-
| QA Contact
| For bug resolution. Default is also to dave.null@w3.org
| 
|-
| CC:
| Any valid email. Default is Eliot and Doug right now.
| 
|-
| URL:
| Locator for the page that the bug references
| 
|-
| Summary
| Brief summary of the bug
| Yes
|-
| Description
| Detailed description of the bug
| 
|-
| Attachment
| method by with images, supporting files, etc. can be attached to bug
| 
|-
| Keywords
| For categorizing bugs, i.e. ''Infrastructure''
| 
|-
| Depends on
| List of bugs that this bug is dependent on
| 
|-
| Blocks
| List of bugs blocked by this bug
| 
|}

==Creating a bug==
To create a new bug, just click ''New'' on one of the Bugzilla pages. When you create a new bug, you must select ''webplatform.org'' as the product. The form that follows contains the fields listed above. 


==Commenting on a bug==

Once a bug is open, you merely add a comment in the Comment field and then click ''Save changes''. Bugzilla saves the comments in order. You can comment in general on the bug or reply to a specific comment already in the bug's history. 

==Resolving bugs==

To resolve a bug, merely change the status to ''RESOLVED''. A new dropdown menu appears listing choices for how the bug was resolved. After making the selection and adding any appropriate comments, save changes.

==Access and permissions==

The WPD Bugzilla database is open only to those who have a current W3C account. This includes W3C staff members, WPD stewards, members of working groups, and members of W3C Community Groups. WPD is looking at ways that this database may be opened to the public in the future.
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}