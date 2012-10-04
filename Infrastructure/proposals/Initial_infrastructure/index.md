==Work Items==

{| class="wikitable sortable"
! Priority
! Owner
! Task
! Status
! Time Estimate
! Depends On
! Must Finish By
|-
| 1
| Ryan
| New URL structure
| complete
| 2-5 hours
| DNS changes
| Sep 28
|-
| 1
| Ryan
| Fastly integration
| complete
| 1 hour
| New URL structure
| Sep 28
|-
| 2
| Ryan
| Review code (extensions and SemMediaWiki)
|  in progress                                      
| 1-2 hours
| None
| Sep 28
|-
| 2
| Ryan
| Move to DB service
|                                        
| 1-2 hours
| None
| Sep 28
|-
| 1
| Ryan
| Backups/Restore instructions
| in progress                                
| 2-5 hours
| None
| Sep 28
|-
| 1
| Ryan
| Move to Block Service for gluster and backups
| complete
| 1-2 hours
| None
| Sep 28
|-
| 1
| Ryan
| Staging Server
| complete
| 4-5 hours
| New URL structure
| Sep 28
|-
| 1
| Ryan
| Improve deploy system
| complete
| 1 hour
| None
| Sep 28
|-
| 1
| Ryan
| Fix deployment code to output results
| open
| 1-2 hours
| None
| Sep 28
|-
| 2
| Ryan
| Move to object storage for media uploads
|                                        
| 4-5 hours
| Need to ask Wikimedia about how it works
| Sep 28
|-
| 1
| Ryan
| Launch add'l app server instances
| complete
| 1-2 hours (took 4 hours)
| None
| Sep 28
|-
| 1
| Ryan
| Add ganglia monitoring
| complete
| 1-2 hours
| None
| Oct 1
|-
| 1
| Ryan
| Add nagios monitoring
| complete
| 2-4 hours
| None
| ?
|-
| 1
| Ryan
| Add database replication
| complete
| 1-2 hours
| None
| Oct 3
|-
| 1
| Contractors
| Import script (MSDN to Semantic MediaWiki)
| in progress                                       
| 
| 
| Sep 28
|-
| 1
| Contractors
| Comments extension (HW)
| in progress, 90% complete                                       
| 10 days
| partly on Skinning
| Sep 28
|-
| 1
| Contractors
| Site metrics (HW)
| done                                       
| 2 days
| Improve deploy system (?)
| Sep 28
|-
| 1
| Contractors
| Integration with other software (Single Sign-On): Wordpress (HW)
| in progress                                     
| 2 days
| 
* Installation of Wordpress
* Launch add'l app server instances 
| Sep 28
|-
| 1
| Contractors
| Integration with other software (Single Sign-On): Questions2Answers (HW)
| in progress                                   
| 3 days
| 
* Installation of Questions2Answers
* Launch add'l app server instances 
| Sep 28
|-
| 1
| Contractors
| Search extension (page titles, categories) (HW)
| odone                                       
| 3 days
| partly on Skinning
| Sep 28
|-
| 3
| Contractors
| Translation extension (HW)
| postponed                                       
| 8 days
| partly on Skinning
| Sep 28
|-
| 1
| Contractors
| Breadcrumbs extension (HW?)
| work in progress                                       
| 
| 
| Sep 28
|-
| 1
| Contractors
| Skinning (HW?)
| work in progress                                       
| 
| 
| Sep 28
|-
| 3
| Contractors
| file upload and storage
| postponed                                   
| 
| 
| Sep 28
|}




===WikiWorks SOW===
====Phase 1====
* Bring up an initial version of MediaWiki on our hosting service that makes best available use of the resources available
* Lock down the initial version of the site so only whitelisted users can access before it launches
* Set up an account system that has normal users and administrators
* Set up webplatform.org to point to the wiki
* Get the MediaWiki configured to work with the CDN (e.g. Fastly), including sending site availability notices to team members
* Set up the ~10 Semantic MediaWiki forms for different types of article content (e.g. CSS Reference, Tutorial, User page, etc.)

====Phase 2====
* Implement a theme design in MediaWiki based on provided designs, and iterate on the implementation and design in response to feedback from the committee.
* Import ~3,000 documents from their existing, disparate sources into as consistent a format as reasonably possible
* Teach the committee members how to create their own Semantic MediaWiki forms
* Advise on best practices for running and configuring a wiki running on Semantic MediaWiki
* Ensure that only administrators can create costly Semantic MediaWiki queries
* Various other required minor tasks leading up to the launch that may arise

===Scraps===
* Fast.ly CDN
* Forums (Q2A)
* Internationalization
* IRC channel #webplatform
* Email feedback account set up
* Federated Login feature
* Comments
* Accessibility
* Blog
* Deployment script for site
* Issue tracker (bugs)
* Language switching
* Logging bot (IRC)
* Metrics and tracking
* Single sign in (SSO)
* System backup of site
* Sandbox (live viewer)
* Required email address for accounts
* Twitter account @webplatform
* Web client (IRC)
* Wiki Setup