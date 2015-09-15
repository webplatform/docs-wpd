---
title: Initial infrastructure
uri: 'WPD:Infrastructure/proposals/Initial infrastructure'

---
**Note**: This page describes the initial plan for webplatform.org, most content is deprecated

## <span>Work Items</span>

<table>
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<col width="14%" />
<thead>
<tr class="header">
<th align="left">Priority</th>
<th align="left">Owner</th>
<th align="left">Task</th>
<th align="left">Status</th>
<th align="left">Time Estimate</th>
<th align="left">Depends On</th>
<th align="left">Must Finish By</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">New URL structure</td>
<td align="left">complete</td>
<td align="left">2-5 hours</td>
<td align="left">DNS changes</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Fastly integration</td>
<td align="left">complete</td>
<td align="left">1 hour</td>
<td align="left">New URL structure</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">2</td>
<td align="left">Ryan</td>
<td align="left">Review code (extensions and SemMediaWiki)</td>
<td align="left">in progress</td>
<td align="left">1-2 hours</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Ryan</td>
<td align="left">Move to DB service</td>
<td align="left"></td>
<td align="left">1-2 hours</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Backups/Restore instructions</td>
<td align="left">in progress</td>
<td align="left">2-5 hours</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Move to Block Service for gluster and backups</td>
<td align="left">complete</td>
<td align="left">1-2 hours</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Staging Server</td>
<td align="left">complete</td>
<td align="left">4-5 hours</td>
<td align="left">New URL structure</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Improve deploy system</td>
<td align="left">complete</td>
<td align="left">1 hour</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Fix deployment code to output results</td>
<td align="left">open</td>
<td align="left">1-2 hours</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Ryan</td>
<td align="left">Move to object storage for media uploads</td>
<td align="left"></td>
<td align="left">4-5 hours</td>
<td align="left">Need to ask Wikimedia about how it works</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Launch add'l app server instances</td>
<td align="left">complete</td>
<td align="left">1-2 hours (took 4 hours)</td>
<td align="left">None</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Add ganglia monitoring</td>
<td align="left">complete</td>
<td align="left">1-2 hours</td>
<td align="left">None</td>
<td align="left">Oct 1</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Add nagios monitoring</td>
<td align="left">complete</td>
<td align="left">2-4 hours</td>
<td align="left">None</td>
<td align="left"> ?</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Ryan</td>
<td align="left">Add database replication</td>
<td align="left">complete</td>
<td align="left">1-2 hours</td>
<td align="left">None</td>
<td align="left">Oct 3</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Import script (MSDN to Semantic MediaWiki)</td>
<td align="left">in progress</td>
<td align="left"></td>
<td align="left"></td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Comments extension (HW)</td>
<td align="left">in progress, 90% complete</td>
<td align="left">10 days</td>
<td align="left">partly on Skinning</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Site metrics (HW)</td>
<td align="left">done</td>
<td align="left">2 days</td>
<td align="left">Improve deploy system (?)</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Integration with other software (Single Sign-On): Wordpress (HW)</td>
<td align="left">in progress</td>
<td align="left">2 days</td>
<td align="left"><ul>
<li>Installation of Wordpress</li>
<li>Launch add'l app server instances</li>
</ul></td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Integration with other software (Single Sign-On): Questions2Answers (HW)</td>
<td align="left">in progress</td>
<td align="left">3 days</td>
<td align="left"><ul>
<li>Installation of Questions2Answers</li>
<li>Launch add'l app server instances</li>
</ul></td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Search extension (page titles, categories) (HW)</td>
<td align="left">odone</td>
<td align="left">3 days</td>
<td align="left">partly on Skinning</td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">Contractors</td>
<td align="left">Translation extension (HW)</td>
<td align="left">postponed</td>
<td align="left">8 days</td>
<td align="left">partly on Skinning</td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Breadcrumbs extension (HW?)</td>
<td align="left">work in progress</td>
<td align="left"></td>
<td align="left"></td>
<td align="left">Sep 28</td>
</tr>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contractors</td>
<td align="left">Skinning (HW?)</td>
<td align="left">work in progress</td>
<td align="left"></td>
<td align="left"></td>
<td align="left">Sep 28</td>
</tr>
<tr class="even">
<td align="left">3</td>
<td align="left">Contractors</td>
<td align="left">file upload and storage</td>
<td align="left">postponed</td>
<td align="left"></td>
<td align="left"></td>
<td align="left">Sep 28</td>
</tr>
</tbody>
</table>

### <span>WikiWorks SOW</span>

#### <span>Phase 1</span>

-   Bring up an initial version of MediaWiki on our hosting service that makes best available use of the resources available
-   Lock down the initial version of the site so only whitelisted users can access before it launches
-   Set up an account system that has normal users and administrators
-   Set up webplatform.org to point to the wiki
-   Get the MediaWiki configured to work with the CDN (e.g. Fastly), including sending site availability notices to team members
-   Set up the \~10 Semantic MediaWiki forms for different types of article content (e.g. CSS Reference, Tutorial, User page, etc.)

#### <span>Phase 2</span>

-   Implement a theme design in MediaWiki based on provided designs, and iterate on the implementation and design in response to feedback from the committee.
-   Import \~3,000 documents from their existing, disparate sources into as consistent a format as reasonably possible
-   Teach the committee members how to create their own Semantic MediaWiki forms
-   Advise on best practices for running and configuring a wiki running on Semantic MediaWiki
-   Ensure that only administrators can create costly Semantic MediaWiki queries
-   Various other required minor tasks leading up to the launch that may arise

### <span>Scraps</span>

-   Fast.ly CDN
-   Forums (Q2A)
-   Internationalization
-   IRC channel \#webplatform
-   Email feedback account set up
-   Federated Login feature
-   Comments
-   Accessibility
-   Blog
-   Deployment script for site
-   Issue tracker (bugs)
-   Language switching
-   Logging bot (IRC)
-   Metrics and tracking
-   Single sign in (SSO)
-   System backup of site
-   Sandbox (live viewer)
-   Required email address for accounts
-   Twitter account @webplatform
-   Web client (IRC)
-   Wiki Setup
