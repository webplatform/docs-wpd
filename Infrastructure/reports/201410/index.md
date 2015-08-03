---
title: WPD:Infrastructure/reports/201410
---
<h1><span class="mw-headline" id="October_2014_sprint_report">October 2014 sprint report</span></h1>
<p>This sprint is about refactoring the full server infrastructure to ease the maintenance work and automate what’s possible.
</p><p>In order to get more details on the work that has been done, refer to <a href="/wiki/WPD:Infrastructure/analysis/2014-Improvements_plan" title="WPD:Infrastructure/analysis/2014-Improvements plan"><i>2014 Improvements plan</i> page</a>
</p><p><br />
</p>
<h2><span class="mw-headline" id="Goal">Goal</span></h2>
<p>The goal of this sprint is to have a separation between <i>development</i> (e.g. a local Vagrant VM, or code checkout), <i>staging</i> (i.e. a full deployment) and <i>production</i> (i.e. the live site) so we can test our changes in an environment without impacting the live "production" site.
</p>
<h2><span class="mw-headline" id="Requirements">Requirements</span></h2>
<ol><li> Every VMs w/ up to date softwares (database server, linux, etc)</li>
<li> Every web application to work under SSL</li>
<li> Every web applications are built on top of a Git release our customizations patched on top of them, see <a href="#Updating_the_web_applications">#Updating the web applications</a></li>
<li> Refactor server configuration scripts in a way such that we can have a fully working clone of the production site. Without impacting it. </li>
<li> Everything has to be public, except passwords and private keys</li>
<li> Setup a system such that if a module gets merged to a specific branch triggers an automatic update of the code on the servers</li>
<li> Setup a staging version of the site that replicates everything in a separate OpenStack project. Any component of the site could be used by adding 'staging' to it.</li>
<li> Set in place a system that "listens" to given GitHub repository to update the related component. See <a href="#Automatic_updates">#Automatic updates</a></li></ol>
<p>In other words, we should be able to work on anything in; webplatform<i>Staging</i>.org as a "sandbox" (i.e. do not touch live "production" site), which will allow anybody to replicate the full environment regardless of where its hosted or which top level domain name its being used.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Expected_outcome">Expected outcome</span></h2>
<ul><li> Have a COMPLETELY INDEPENDENT set of Virtual Machines to serve the FULL public facing webplatform.org components (i.e. blog, docs, project.webplatform.org)</li>
<li> Before deploying to production, every components MUST be running fine on <i>webplatformSTAGING.org</i> (a.k.a. "<b>staging</b>")</li>
<li> Deploy automatically on git push (GitHub hooks) on master branch and/or a release tag (TBD)</li>
<li> Self-contained environment at every level; e.g, <i>staging</i> MUST NOT use any resources from <i>production</i></li>
<li> Full clone of the site for each components; e.g. <b>blog.webplatform.org</b> (production), <b>blog.webplatformSTAGING.org</b> (staging).</li>
<li> Harmonize configuration settings across the softwares, automate them based on known data facts, do not rely on internal DNS</li>
<li> Remove anything that isn’t used anymore, and simplify system as much as possible</li></ul>
<h2><span class="mw-headline" id="Tasks_summary">Tasks summary</span></h2>
<p>... tasks details are in <a href="/wiki/WPD:Infrastructure/analysis/2014-Improvements_plan" title="WPD:Infrastructure/analysis/2014-Improvements plan">WPD:Infrastructure/analysis/2014-Improvements_plan</a>
</p>
<ul><li> Publish to the public all our deployment scripts, with correct author attribution, without passwords nor private data</li>
<li> Set in place a system that will update code automatically when a contributor push on watched Git repos</li>
<li> Salt reactor pull, and run scripts (bower, grunt, composer, etc) and makes a zip archive, deploy archive</li>
<li> Salt reactor launch rsync when changes are detected</li>
<li> Ensure all components works on BOTH <b>webplatform.org</b> AND <b>webplatformSTAGING.org</b> top level domains, <i>without configuration switches</i></li>
<li> Ensure all VM are on Ubuntu 14.04 LTS</li>
<li> Make sure every components are working as it should</li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Status">Status</span></h2>
<p><b>NOTE</b>: Project is completed.
</p>
<ul><li> Missing web apps;
<ul><li> webat25.org (won’t be migrated, we will convert as a static site by May 2015)</li></ul></li>
<li> Set in place automation, see <a href="#Automatic_updates">#Automatic updates</a></li></ul>
<p><br />
</p>
<h2><span class="mw-headline" id="Intervention_plan">Intervention plan</span></h2>
<h3><span class="mw-headline" id="Updating_the_web_applications">Updating the web applications</span></h3>
<p>For each web application:
</p>
<ul><li> Pick a version from GitHub, fork in our repo</li>
<li> Get anything that’s not source-controlled in our code, make it as a patch on top of the original code</li>
<li> Make sure the web app looks fine with the current CSS</li>
<li> Make sure the configuration is adjusted by salt stack, nothing manual</li>
<li> Make sure the theme doesn’t refer to production site, but current deployment</li>
<li> Make sure that the assets are protocol relative (i.e. if site over SSL, call images and other assets through SSL too, keeping the bar "green")</li></ul>
<p>Later, we’ll have a system that listens and updates the site automatically.
</p>
<h3><span class="mw-headline" id="Automatic_updates">Automatic updates</span></h3>
<p>A system that listens to new version tags on given GitHub repositories.
</p><p>Once a tag is made, the staging salt master should;
</p>
<ol><li> pull in the changes</li>
<li> run any update scripts (sass, docpad, composer, etc)</li>
<li> update all applicable web servers</li></ol>
<p>More to come. This is the current next step.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:30970-0!*!0!!*!*!*!esi=1 and timestamp 20150731185631 and revision id 101347
 -->
