---
title: Monit
uri: 'WPD:Infrastructure/Monitoring/Monit'

---
## What is Monit

[Monit](http://mmonit.com/monit/) is a server monitoring system that ensures that their services are running or enforce them to run.

[Monit](http://mmonit.com/monit/) has two components:

-   **monit**, an open-source agent with internal reporting
-   **M/Monit**, a paid software that *monit* can push updates to

## Monit

As described in the Feb. 2015 documentation rework describing the [Base configuration of a VM](/WPD:Infrastructure/architecture/Base_configuration_of_a_VM), every VM has Monit running.

You can review the Monit report by following steps described in [Reports to review a VM status, at *Using Monit* section](/WPD:Infrastructure/architecture/Reports_to_review_status#Using_Monit).

Here is a preview of how a Monit status report looks like.

![20150224-monit-status-preview.png](/WPD/assets/public/5/5d/20150224-monit-status-preview.png)

## *M/Monit*

Those arescreenshots of **M/Monit** while I was testing out the feature differences between the paid app (*M/Monit*) and what comes in the open source version.

-   ![monit dashboard 201502 status.png](/WPD/assets/public/a/a1/monit_dashboard_201502_status.png)
-   ![monit dashboard 201502 stats.png](/WPD/assets/public/5/5b/monit_dashboard_201502_stats.png)
-   ![monit dashboard 201502 home.png](/WPD/assets/public/5/52/monit_dashboard_201502_home.png)
-   ![monit dashboard 201502 vm detail.png](/WPD/assets/public/f/f2/monit_dashboard_201502_vm_detail.png)
