What follows is an attempt to document my findings while skinning The Bug Genie in the form of a short guide that I wish I had found when I started skinning it for WebPlatform.org. Most of it is reverse engineered, so there might be small inaccuracies.

== Where is the HTML located? ==

Bug Genie is split into multiple modules, so the templates are scattered across multiple folders. The most common UI elements are found in the following paths:

=== core/templates ===

Very few templates, but the most crucial:

* <code>backdrops.inc.php</code>: The various popup dialogs
* <code>footer.inc.php</code>: The footer at the end of every page
* <code>headertop.inc.php</code>: The top part of the header. In the default BG it contains the logo, byline and global popup menus. In WPD it contains the logo, search and user menu.
* <code>submenu.inc.php</code>: Breadcrumbs & search in the default skin. In WPD it’s used for the global navigation (DOCS etc).
* <code>layout.php</code>: The main markup shell around the content. In the default BG it contains a main table which is around the content of every page, but it seems it can be safely removed.
* <code>offline.inc.php</code>: Message for when the site is offline. Not customized in WPD.
* <code>error.php</code>: A full page template about technical errors (e.g. can't connect to the database). Not customized in WPD.
* <code>toolarea.inc.php</code>: Custom WPD template, not present in the default BG. 

=== modules/main/templates ===

We didn’t customize any of those for WPD, but the templates for many important features reside here.

=== modules/project/templates ===

Lots of useful templates here too. The distinction between <code>modules/main</code> and <code>modules/project</code> is a bit unclear. The only template here that we customized for WPD is <code>_overview.inc.php</code> which contains the project list in the home page.

== Can I add a new template? ==

Adding templates is actually pretty easy. For example, to create a new Core template:

# Make a new <code>.inc.php</code> file in <code>core/templates</code>. In fact it could have any extension, but <code>.inc.php</code> is consistent with the other templates.
# Include whatever code or markup you want in it. I've also noticed that moving code across templates seems to work fine, unlike in other software. However, I haven't tested that very extensively.
# In the place where you want the template to be included, use the following line of code (assuming the new template is called <code>toolarea.inc.php</code>:
	
	<pre>&lt;?php require THEBUGGENIE_CORE_PATH . 'templates/toolarea.inc.php'; ?></pre>
	
There are probably other constants similar to <code>THEBUGGENIE_CORE_PATH</code> for the other template paths, but I didn't need to look into that.

There is also a <code>include_template()</code> function that accepts a path (e.g. <code>'project/milestonedetailsissue'</code>) and an associative array of parameters.

== PHP in templates ==

PHP in templates is kept to a minimum, to adhere to a proper MVC-style separation. It’s only used for:

* Conditionals (if)
* Looping
* Template functions (see section below for a few of those)
* Basic PHP functions like <code>isset()</code>

The syntax for the control structures is the [http://php.net/manual/en/control-structures.alternative-syntax.php alternative, longer one] to make them clearer, similarly to other software using PHP for templating, like Wordpress.

== Functions used in templates ==

These are PHP functions used inside <code><?php</code> and <code>?></code>.

* <code>__()</code> prints internationalized phrases. In English it makes no difference, but in other languages, it will print out the translation of the parameter. This is how all content phrases should be printed out. 
* <code>make_url()</code> [http://issues.thebuggenie.com/wiki/TheBugGenie%3ADevelopment%3ARouting#article_149_toc_3 Makes internal URLs]
* <code>link_tag()</code> prints out an HTML link (<code><a href></code>). It accepts three parameters:
** URL: The <code>href</code> attribute
** content: The link text (i.e. the content of the tag)
** attributes: A PHP associative array of HTML attributes
* <code>image_tag()</code> prints out an HTML image tag (<code>&lt;img></code>). It accepts two parameters:
** URL: The <code>src</code> attribute
** attributes: A PHP associative array of HTML attributes
* <code>javascript_link_tag()</code> same as link_tag() with a URL of <code>"javascript:void(0)"</code>