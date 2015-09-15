---
title: Maintaining Varnish/Fastly configuration
uri: 'WPD:Infrastructure/procedures/Maintaining Varnish or Fastly configuration'

---
### <span>[WebPlatform server Infrastructure architecture menu](/WPD:Infrastructure/architecture)</span>

-   [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM)
-   [Reports to review status](/WPD:Infrastructure/architecture/Reports_to_review_status)
-   [Roles and environment level](/WPD:Infrastructure/architecture/Roles_and_environment_level)
-   [SSL certificates](/WPD:Infrastructure/architecture/SSL_certificates)
-   [The salt master](/WPD:Infrastructure/architecture/The_salt_master)
-   [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
-   [Useful commands](/WPD:Infrastructure/architecture/Useful_commands)
-   [VM roles](/WPD:Infrastructure/architecture/VM_roles)

**See also**

-   [Deploying code changes](/WPD:Infrastructure/procedures/Deploying_code_changes)
-   [Replacing a VM](/WPD:Infrastructure/procedures/Replacing_a_VM)
-   **Maintaining Fastly configuration**
-   [Managing MySQL replication](/WPD:Infrastructure/procedures/Managing_MySQL_replication)
-   [Create new database credentials and configure a web application to use it](/WPD:Infrastructure/procedures/Create_new_database_credentials_configure_a_web_application_to_use_it)
-   [Maintaining ElasticSearch cluster](/WPD:Infrastructure/procedures/Maintaining_ElasticSearch_cluster)
-   [Maintaining email services](/WPD:Infrastructure/procedures/Maintaining_email_services)

The following summarizes how to manage our Varnish caching service served by our friends at [Fastly](https://fastly.com). Note that the documentation describes how Varnish works but also how to manage Fastly very own Varnish cluster so we don’t have to.

This document is specific on how to maintain Varnish configuration at Fastly. Notes that describes the specifics of things we should keep in mind when configuring the cache should be moved to [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)

## <span>Abastract</span>

If your system uses cookies, which is most of the time the case, Varnish does not caches. The configuration MUST to be adjusted to each site specifics. Details such as a web application sending HTTP headers such as Cache-Control, Set-Cookie, Cookie can still prevent caching to happen.

This page is about keeping notes on current Varnish configuration files and notes to help maintaining an appropriate caching strategy.

## <span>NOTES</span>

### <span>Varnish version and limitations</span>

An important detail to remember is that Fastly is using Varnish 2.1.4, their configuration specifics do not support either pipe, ban, nor purging with ACL.

Also, the way to provide CDN service is with what they call "Shield", it is basically a layer of application that stores a local copy of what is grabbed by a service backend server. Provided that the backend server do not explicitly prevent caching, or that the VCL has appropriate adjustments, Fastly will send files from the Shield before hitting again the backend servers.

VCL is the Varnish Configuration language file, throughout the panel, we can see two VCL buttons, the one beside the service name and revision is to download the generated VCL, whereas we can also provide our own VCL that must have keywords so the panel adds content to it.

A recommended way to work is to follow **[How do I mix and match Fastly VCL with custom VCL](https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-)**

### <span>Details to consider</span>

#### <span>MediaWiki</span>

Here are the specifics for MediaWiki

-   Note that most of the cookies starts with the *\$wgDBname* string from the *Settings\*.php* file. In the list below, its value is 'wpwiki'.
-   Delete all cookies, except: wpwikiUserID, wpwiki\_session, wpwikiUserName, Token, LoggedOut, dismissSiteNotice
-   Only place to set cookies are when UserLogin, UserLogout

**Reminder** more notes about specifics for each web application we deployed are noted in [**Things to consider when we expose service via Fastly and Varnish**](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)

## <span>Accessing VCL configuration from Fastly</span>

To access/overwrite the file in Fastly, go to: ![20131121-Fastly-vcl-buttons.png](/WPD/assets/public/6/68/20131121-Fastly-vcl-buttons.png)

-   [Fastly pannel](https://app.fastly.com/), login
-   Select targeted site (e.g. *docs.webplatform.org*)
-   Configure tab on top, Configure button
-   VCL on the left

#### <span>Wizard to add a backend host</span>

While describing how to debug an issue we had with Semantic MediaWiki, I described how to change which public IPs would be proxyed by Fastly.

The screenshot below is described in [WPD:Infrastructure/procedures/Rebuilding\_Semantic\_Media\_Wiki\_when\_job\_queue\_is\_going\_out\_of\_control](/WPD:Infrastructure/procedures/Rebuilding_Semantic_Media_Wiki_when_job_queue_is_going_out_of_control)

![fastly-docs-service-hosts-screenshot.png](/WPD/assets/public/f/fb/fastly-docs-service-hosts-screenshot.png)

### <span>Current Fastly configuration</span>

Make the content of snippet as a file and upload it to the Fastly control pannel.

Configuration files are stored on [Github, in **webplatform/varnish-configs** project](https://github.com/webplatform/varnish-configs), the VCL file name should match the subdomain and also the service bane in Fastly dashboard.

## <span>Reference</span>

-   [Fastly: How to mix and match Fastly VCL with custom VCL (Varnish configuration file)](https://fastly.zendesk.com/entries/23206371-How-do-I-mix-and-match-Fastly-VCL-with-custom-VCL-)
-   [**WebPlatform** varnish-configs GitHub repository](https://github.com/webplatform/varnish-configs)
-   See also more notes on the topic at [Things to consider when we expose service via Fastly and Varnish](/WPD:Infrastructure/architecture/Things_to_consider_when_we_expose_service_via_Fastly_and_Varnish)
