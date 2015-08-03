---
title: WPD:Infrastructure/Monitoring/Monit
---
<h1><span class="mw-headline" id="Monit">Monit</span></h1>
<h2><span class="mw-headline" id="What_is_Monit">What is Monit</span></h2>
<p><a rel="nofollow" class="external text" href="http://mmonit.com/monit/">Monit</a> is a server monitoring system that ensures that their services are running or enforce them to run. 
</p><p><a rel="nofollow" class="external text" href="http://mmonit.com/monit/">Monit</a> has two components:
</p>
<ul><li> <b>monit</b>, an open-source agent with internal reporting</li>
<li> <b>M/Monit</b>, a paid software that <i>monit</i> can push updates to</li></ul>
<h2><span class="mw-headline" id="Monit_2">Monit</span></h2>
<p>As described in the Feb. 2015 documentation rework describing the <a href="/wiki/WPD:Infrastructure/architecture/Base_configuration_of_a_VM" title="WPD:Infrastructure/architecture/Base configuration of a VM">Base configuration of a VM</a>, every VM has Monit running.
</p><p>You can review the Monit report by following steps described in <a href="/wiki/WPD:Infrastructure/architecture/Reports_to_review_status#Using_Monit" title="WPD:Infrastructure/architecture/Reports to review status">Reports to review a VM status, at <i>Using Monit</i> section</a>.
</p><p>Here is a preview of how a Monit status report looks like.
</p><p><a href="/wiki/File:20150224-monit-status-preview.png" class="image"><img alt="20150224-monit-status-preview.png" src="//static.webplatform.org/w/public/5/5d/20150224-monit-status-preview.png" width="1079" height="850" /></a>
</p><p><br />
</p>
<h2><span class="mw-headline" id="M.2FMonit"><i>M/Monit</i></span></h2>
<p>Those arescreenshots of <b>M/Monit</b> while I was testing out the feature differences between the paid app (<i>M/Monit</i>) and what comes in the open source version.
</p>
<ul><li> <a href="/wiki/File:monit_dashboard_201502_status.png" class="image"><img alt="monit dashboard 201502 status.png" src="//static.webplatform.org/w/public/a/a1/monit_dashboard_201502_status.png" width="1043" height="739" /></a></li>
<li> <a href="/wiki/File:monit_dashboard_201502_stats.png" class="image"><img alt="monit dashboard 201502 stats.png" src="//static.webplatform.org/w/public/5/5b/monit_dashboard_201502_stats.png" width="1418" height="839" /></a></li>
<li> <a href="/wiki/File:monit_dashboard_201502_home.png" class="image"><img alt="monit dashboard 201502 home.png" src="//static.webplatform.org/w/public/5/52/monit_dashboard_201502_home.png" width="2406" height="1436" /></a> </li>
<li> <a href="/wiki/File:monit_dashboard_201502_vm_detail.png" class="image"><img alt="monit dashboard 201502 vm detail.png" src="//static.webplatform.org/w/public/f/f2/monit_dashboard_201502_vm_detail.png" width="1040" height="685" /></a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:58578-0!*!0!!*!5!*!esi=1 and timestamp 20150731185659 and revision id 100845
 -->
