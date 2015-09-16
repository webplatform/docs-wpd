---
title: WPD:Infrastructure
uri: 'WPD:Infrastructure'

---
## Table of contents

Listing all sub pages from here.

-   [Bugs](/WPD:Infrastructure/Bugs)
-   [Components](/WPD:Infrastructure/Components)
    -   [Code Viewer](/WPD:Infrastructure/Components/Code_Viewer)
    -   [CompaTables](/WPD:Infrastructure/Components/CompaTables)
    -   [Docs pages analytics](/WPD:Infrastructure/Components/Docs_pages_analytics)
    -   [WebPlatformMediaWikiExtensionBundle](/WPD:Infrastructure/Components/WebPlatformMediaWikiExtensionBundle)
    -   [email](/WPD:Infrastructure/Components/email)
-   [Monitoring](/WPD:Infrastructure/Monitoring)
    -   [Monit](/WPD:Infrastructure/Monitoring/Monit)
-   [analysis](/WPD:Infrastructure/analysis)
    -   [2013-Hardware and software requirements](/WPD:Infrastructure/analysis/2013-Hardware_and_software_requirements)
    -   [2013-Migrating to a new cloud provider](/WPD:Infrastructure/analysis/2013-Migrating_to_a_new_cloud_provider)
    -   [2013-Usage and future state](/WPD:Infrastructure/analysis/2013-Usage_and_future_state)
    -   [2014-Improvements plan](/WPD:Infrastructure/analysis/2014-Improvements_plan)
    -   [2014-OAuth study notes](/WPD:Infrastructure/analysis/2014-OAuth_study_notes)
    -   [2015-How MediaWiki backend sees requests with or without Fastly in front](/WPD:Infrastructure/analysis/2015-How_MediaWiki_backend_sees_requests_with_or_without_Fastly_in_front)
    -   [Things to ensure is not changed](/WPD:Infrastructure/analysis/Things_to_ensure_is_not_changed)
-   [architecture](/WPD:Infrastructure/architecture)
    -   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
    -   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
    -   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
    -   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
    -   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
    -   [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
    -   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
    -   [VM roles](/WPD:Infrastructure/architecture/VM_roles)
-   [priorities](/WPD:Infrastructure/priorities)
-   [procedures](/WPD:Infrastructure/procedures)
    -   [Create a public download archive repository stored directly in DreamObjects](/WPD:Infrastructure/procedures/Create_a_public_download_archive_repository_stored_directly_in_DreamObjects)
    -   [Create new database credentials configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
    -   [Creating mail service infrastructure](/WPD:Infrastructure/procedures/Creating_mail_service_infrastructure)
    -   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
    -   [Design changes guide](/WPD:Infrastructure/procedures/Design_changes_guide)
    -   [How to maintain accounts](/WPD:Infrastructure/procedures/How_to_maintain_accounts)
    -   [Importing data into MediaWiki](/WPD:Infrastructure/procedures/Importing_data_into_MediaWiki)
    -   [Installing and theme Firefox accounts](/WPD:Infrastructure/procedures/Installing_and_theme_Firefox_accounts)
    -   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
    -   [Maintaining Varnish or Fastly configuration](/WPD:Infrastructure/procedures/Maintaining_Varnish_or_Fastly_configuration)
    -   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)
    -   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
    -   [Piwik Tracking code installation](/WPD:Infrastructure/procedures/Piwik_Tracking_code_installation)
    -   [Rebuilding Semantic Media Wiki when job queue is going out of control](/WPD:Infrastructure/procedures/Rebuilding_Semantic_Media_Wiki_when_job_queue_is_going_out_of_control)
    -   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
    -   [Testing service availability](/WPD:Infrastructure/procedures/Testing_service_availability)
    -   [Typical wiki maintenance tasks](/WPD:Infrastructure/procedures/Typical_wiki_maintenance_tasks)
    -   [When The Bug Genie mailing queue is broken](/WPD:Infrastructure/procedures/When_The_Bug_Genie_mailing_queue_is_broken)
-   [proposals](/WPD:Infrastructure/proposals)
    -   [Initial infrastructure](/WPD:Infrastructure/proposals/Initial_infrastructure)
    -   [Logging aggregation and analytics](/WPD:Infrastructure/proposals/Logging_aggregation_and_analytics)
    -   [Maintenance workflows](/WPD:Infrastructure/proposals/Maintenance_workflows)
    -   [Site Map](/WPD:Infrastructure/proposals/Site_Map)
    -   [Site status problem notification messages](/WPD:Infrastructure/proposals/Site_status_problem_notification_messages)
-   [reports](/WPD:Infrastructure/reports)
    -   [201410](/WPD:Infrastructure/reports/201410)
    -   [201503](/WPD:Infrastructure/reports/201503)

## Site Structure

|Resource|Software|URL structure|Deployed|
|:-------|:-------|:------------|:-------|
|landing page|[(project on github)](https://github.com/webplatform/www.webplatform.org)|[webplatform.org/](http://webplatform.org/)|yes|
|wiki|[MediaWiki](https://www.mediawiki.org/wiki/MediaWiki)|[docs.webplatform.org/wiki/](https://docs.webplatform.org/wiki/)|yes|
|IRC logger|[Lumberjack (now called Pierc)](http://classam.github.io/pierc/)|[www.webplatform.org/talk/chatlogs/](https://www.webplatform.org/talk/chatlogs/)|yes|
|metrics|[Piwik](http://piwik.org/)|[stats.webplatform.org/](https://stats.webplatform.org/)|yes|
|blog|[WordPress](http://wordpress.org/)|[blog.webplatform.org/](https://blog.webplatform.org/)|yes|
|Sandbox|[Dabblet](http://dabblet.com/)|[code.webplatform.org/](http://code.webplatform.org/)|yes|
|Project management and bugs|[The Bug Genie](http://www.thebuggenie.com/)|[project.webplatform.org/](https://project.webplatform.org/)|yes|
|Accounts|[Firefox Accounts](https://wiki.mozilla.org/Identity/Firefox_Accounts)|[accounts.webplatform.org/](https://accounts.webplatform.org/)|yes|

