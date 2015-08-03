---
title: WPD:Skinning the bug genie
---
<h1><span class="mw-headline" id="A_hitchhiker.E2.80.99s_guide_to_skinning_the_Bug_Genie">A hitchhiker’s guide to skinning the Bug Genie</span></h1>
<p>What follows is an attempt to document my findings while skinning The Bug Genie in the form of a short guide that I wish I had found when I started skinning it for WebPlatform.org. Most of it is reverse engineered, so there might be small inaccuracies.
</p>
<h2><span class="mw-headline" id="Where_is_the_HTML_located.3F">Where is the HTML located?</span></h2>
<p>Bug Genie is split into multiple modules, so the templates are scattered across multiple folders. The most common UI elements are found in the following paths:
</p>
<h3><span class="mw-headline" id="core.2Ftemplates">core/templates</span></h3>
<p>Very few templates, but the most crucial:
</p>
<ul><li> <code>backdrops.inc.php</code>: The various popup dialogs</li>
<li> <code>footer.inc.php</code>: The footer at the end of every page</li>
<li> <code>headertop.inc.php</code>: The top part of the header. In the default BG it contains the logo, byline and global popup menus. In WPD it contains the logo, search and user menu.</li>
<li> <code>submenu.inc.php</code>: Breadcrumbs &amp; search in the default skin. In WPD it’s used for the global navigation (DOCS etc).</li>
<li> <code>layout.php</code>: The main markup shell around the content. In the default BG it contains a main table which is around the content of every page, but it seems it can be safely removed.</li>
<li> <code>offline.inc.php</code>: Message for when the site is offline. Not customized in WPD.</li>
<li> <code>error.php</code>: A full page template about technical errors (e.g. can't connect to the database). Not customized in WPD.</li>
<li> <code>toolarea.inc.php</code>: Custom WPD template, not present in the default BG. </li></ul>
<h3><span class="mw-headline" id="modules.2Fmain.2Ftemplates">modules/main/templates</span></h3>
<p>We didn’t customize any of those for WPD, but the templates for many important features reside here.
</p>
<h3><span class="mw-headline" id="modules.2Fproject.2Ftemplates">modules/project/templates</span></h3>
<p>Lots of useful templates here too. The distinction between <code>modules/main</code> and <code>modules/project</code> is a bit unclear. The only template here that we customized for WPD is <code>_overview.inc.php</code> which contains the project list in the home page.
</p>
<h2><span class="mw-headline" id="Can_I_add_a_new_template.3F">Can I add a new template?</span></h2>
<p>Adding templates is actually pretty easy. For example, to create a new Core template:
</p>
<ol><li> Make a new <code>.inc.php</code> file in <code>core/templates</code>. In fact it could have any extension, but <code>.inc.php</code> is consistent with the other templates.</li>
<li> Include whatever code or markup you want in it. I've also noticed that moving code across templates seems to work fine, unlike in other software. However, I haven't tested that very extensively.</li>
<li> In the place where you want the template to be included, use the following line of code (assuming the new template is called <code>toolarea.inc.php</code>:</li></ol>
	<pre>&lt;?php require THEBUGGENIE_CORE_PATH . 'templates/toolarea.inc.php';&#160;?&gt;</pre>
<p>There are probably other constants similar to <code>THEBUGGENIE_CORE_PATH</code> for the other template paths, but I didn't need to look into that.
</p><p>There is also a <code>include_template()</code> function that accepts a path (e.g. <code>'project/milestonedetailsissue'</code>) and an associative array of parameters.
</p>
<h2><span class="mw-headline" id="PHP_in_templates">PHP in templates</span></h2>
<p>PHP in templates is kept to a minimum, to adhere to a proper MVC-style separation. It’s only used for:
</p>
<ul><li> Conditionals (if)</li>
<li> Looping</li>
<li> Template functions (see section below for a few of those)</li>
<li> Basic PHP functions like <code>isset()</code></li></ul>
<p>The syntax for the control structures is the <a rel="nofollow" class="external text" href="http://php.net/manual/en/control-structures.alternative-syntax.php">alternative, longer one</a> to make them clearer, similarly to other software using PHP for templating, like Wordpress.
</p>
<h2><span class="mw-headline" id="Functions_used_in_templates">Functions used in templates</span></h2>
<p>These are PHP functions used inside <code>&lt;?php</code> and <code>?&gt;</code>.
</p>
<ul><li> <code>__()</code> prints internationalized phrases. In English it makes no difference, but in other languages, it will print out the translation of the parameter. This is how all content phrases should be printed out. </li>
<li> <code>make_url()</code> <a rel="nofollow" class="external text" href="http://issues.thebuggenie.com/wiki/TheBugGenie%3ADevelopment%3ARouting#article_149_toc_3">Makes internal URLs</a></li>
<li> <code>link_tag()</code> prints out an HTML link (<code>&lt;a href&gt;</code>). It accepts three parameters:
<ul><li> URL: The <code>href</code> attribute</li>
<li> content: The link text (i.e. the content of the tag)</li>
<li> attributes: A PHP associative array of HTML attributes</li></ul></li>
<li> <code>image_tag()</code> prints out an HTML image tag (<code>&lt;img&gt;</code>). It accepts two parameters:
<ul><li> URL: The <code>src</code> attribute</li>
<li> attributes: A PHP associative array of HTML attributes</li></ul></li>
<li> <code>javascript_link_tag()</code> same as link_tag() with a URL of <code>"javascript:void(0)"</code></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:9377-0!*!*!!*!*!*!esi=1 and timestamp 20150731184401 and revision id 35020
 -->
