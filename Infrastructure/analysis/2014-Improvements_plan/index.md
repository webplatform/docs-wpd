---
title: Sept.-Dec. 2014 Improvement plans
uri: 'WPD:Infrastructure/analysis/2014-Improvements plan'

---
This sprint is about refactoring the server infrastructure to ease the maintenance work and automate what’s possible.

For the project summary, refer to [the 201410 report](/WPD:Infrastructure/reports/201410)

## <span>Tasks</span>

### <span>Done</span>

What has been done and is deployable on staging at this moment.

-   Decommissioned global system features (will improve system and refactor after the rest is ready):
    -   Disabled centralized log
    -   Disabled Ganglia graphs

-   Decommissioned VM types:
    -   storage (we rely on DreamObjects instead of our own)
    -   monitor (we will refactor the monitoring and log management in the next steps)

-   Homepage:
    -   Can be configured (switch `@site.tld` in *docpad.js*) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding.
    -   Supports SSL
    -   Fastly forces SSL
    -   Upgraded version (DocPad)

-   Wiki web app:
    -   Enabled back planned for deprecation extension [SocialProfile Extension](http://www.mediawiki.org/wiki/Extension:SocialProfile), see [issue \#19](https://github.com/webplatform/mediawiki/issues/19). Disabled explicitly uploads, serve an empty 1x1 gif.
    -   Ability to disable completely Piwik tracking
    -   Upgraded version
    -   Supports SSL
    -   Fastly forces SSL
    -   Improved deployment using git
    -   Deployment to exclusively use git submodules (until composer is supported)
    -   Can be configured (switch `siteTopLevelDomain`, in *LocalSettings.php*) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
    -   Improved configuration system to use Salt stack provided values (no manual edition anymore)
    -   Made an extension that contains all copy-pasted micro-extensions, and theme
    -   Migrated all images and fonts to use www.webplatform.org instead (eventually CSS/JS will also be removed)
    -   Have Salt Stack generate config automatically: database, sessions

-   Wiki Compatibility tables extension:
    -   When access `Special:Compatables?topic=css...&action=purge` it also purges keystore copy
    -   Big memory usage was caused by *data.json* being called more than once at EVERY requests (MW arch problem, error somewhere?) — fixed by saving generated HTML AND *data.json* in configurable Keystore

-   Blog web app:
    -   Upgraded version (WordPress)
    -   Improved deployment using git
    -   Reworked skin (see [WebPlatform WordPress theme repo](https://github.com/webplatform/webplatform-wordpress-theme)) to manage theme and plugin configuration through Git. See article: [Managing and deploying WordPress with Git](http://blog.g-design.net/post/60019471157/managing-and-deploying-wordpress-with-git).
    -   Skin can be configured (switch `siteTopLevelDomain`) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
    -   Have Salt Stack generate config automatically: database, sessions

-   Stats web app:
    -   Upgraded version (Piwik)
    -   Improved deployment using git
    -   Reworked skin, forked project and changed theme to match our site theme (there are no real template system nor theme support)
    -   Support SSL
    -   Fastly to force SSL
    -   Config to use database table for sessions (the only one supported off-the-shelf by Piwik so far)
    -   Config points automatically to database and Memcached/Redis IPs

-   Project web app:
    -   Upgraded BugGenie version (BugGenie branch-32)
    -   Skin can be configured (switch `siteTopLevelDomain`) to specify which top level domain to use. Allowing local or staging deployments to keep consistent links without hardcoding
    -   Support SSL
    -   Fastly to force SSL
    -   Config points automatically to database and Memcached IPs

-   Improve error pages:
    -   When backend server crash, before Fastly marks the backend "unhealthy", send link to status page (see [static version](http://www.webplatformstaging.org/errors/503.html))

-   **Upgrade to latest Ubuntu 14.04 LTS version**, and their configured services for each VM types;
    -   notes
    -   bots
    -   db
    -   app
    -   blog
    -   project
    -   memcache
    -   backup
    -   elasticsearch
    -   piwik
    -   source
    -   account
    -   mail

-   Ways to define role of a VM type
    -   Use of Salt mine to store static data such as internal IP addresse for automatic configuration generation
    -   Parse the VM name and make it as a role (e.g. *memcache-jobs1*, has roles: [memcache, jobs]) so we can target secondary service allocation based on the role and not exclusively on the hostname

-   Change Salt stack behavior:
    -   Create a grain to learn in which deployment level (e.g. "staging") we are in
    -   Create a grain to learn what are the roles the VM has (e.g. [salt])

-   Service resiliency subsystem "Monit" XXX:
    -   **Purpose**: Ensure critical services are up
    -   Ensure common service is running: salt-minion, ssh
    -   **Purpose**: Ensure critical services are up
    -   ensure MySQL servers are up on db VM types
    -   ensure Apache HTTP server up on app\*, project\*, blog\*, notes\*, piwik\*, webat\* VM types
    -   ensure Nutcracker is running on app\*, project\*, blog\*, piwik\* VM types
    -   ensure NGINX HTTP server is up on accounts\* VM types
    -   ensure ElasticSearch is up on elastic\* VM types
    -   ensure Memcached is up on memcache\* VM types
    -   ensure alert email config and destination is configured depending of staging/production
    -   ensure disk usage alerts are in place

-   Key store clusters (Memcached, Redis):
    -   **Purpose:** Each cluster fills a role, depending of the life expectancy of the stored data (e.g. sessions should not be cleared, page cache might)
    -   Ensure only local network can connect
    -   Each web app runtime origin VM types should have a **Keystore broker client** (e.g. Nutcracker)

-   Configure **Key store broker client** (Nutcracker):
    -   **Purpose:** Have everything locally is much quicker, this component keeps a local cache, see [MCRouter introduction](https://code.facebook.com/posts/296442737213493/introducing-mcrouter-a-memcached-protocol-router-for-scaling-memcached-deployments/)
    -   Separate port number per use-case, most popular (i.e. will be used most) will use default port number
    -   Use-case 1: Session storage (most popular)
    -   Use-case 2: Keystore (e.g. various components in MediaWiki, etc)
    -   Set `session.save_handler` correctly and consistently

-   NGINX:
    -   Make sure that every vhosts has error page; see `/srv/webplatform/errors`

-   -   *Setup logrotate for non typical logs*: \\[mw-logs, fastly, remote logs\\]

-   **Upgrade to latest Ubuntu 14.04 LTS version**, and their configured services:

-   Blog web app:
    -   Support SSL
    -   Fastly to force SSL
    -   Config W3TotalCache to use local Nutcracker port
    -   Config points automatically to database IP

-   Database cluster, VM types [db]:
    -   Migrate all databases into new cluster using MariaDB 10.1
    -   Ensure every components gets the list of IP addresses of the database servers through Salt stack
    -   Setup replication
    -   Automatic backups, sends to DreamObjects bucket

-   Apache:
    -   Make sure that every vhosts has error page; see `/srv/webplatform/errors`

-   On elastic VM type:
    -   Automatic backups, sends to DreamObjects bucket
