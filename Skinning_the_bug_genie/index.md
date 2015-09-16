---
title: A hitchhiker’s guide to skinning the Bug Genie
uri: 'WPD:Skinning the bug genie'

---
What follows is an attempt to document my findings while skinning The Bug Genie in the form of a short guide that I wish I had found when I started skinning it for WebPlatform.org. Most of it is reverse engineered, so there might be small inaccuracies.

## Where is the HTML located?

Bug Genie is split into multiple modules, so the templates are scattered across multiple folders. The most common UI elements are found in the following paths:

### core/templates

Very few templates, but the most crucial:

-   `backdrops.inc.php`: The various popup dialogs
-   `footer.inc.php`: The footer at the end of every page
-   `headertop.inc.php`: The top part of the header. In the default BG it contains the logo, byline and global popup menus. In WPD it contains the logo, search and user menu.
-   `submenu.inc.php`: Breadcrumbs & search in the default skin. In WPD it’s used for the global navigation (DOCS etc).
-   `layout.php`: The main markup shell around the content. In the default BG it contains a main table which is around the content of every page, but it seems it can be safely removed.
-   `offline.inc.php`: Message for when the site is offline. Not customized in WPD.
-   `error.php`: A full page template about technical errors (e.g. can't connect to the database). Not customized in WPD.
-   `toolarea.inc.php`: Custom WPD template, not present in the default BG.

### modules/main/templates

We didn’t customize any of those for WPD, but the templates for many important features reside here.

### modules/project/templates

Lots of useful templates here too. The distinction between `modules/main` and `modules/project` is a bit unclear. The only template here that we customized for WPD is `_overview.inc.php` which contains the project list in the home page.

## Can I add a new template?

Adding templates is actually pretty easy. For example, to create a new Core template:

1.  Make a new `.inc.php` file in `core/templates`. In fact it could have any extension, but `.inc.php` is consistent with the other templates.
2.  Include whatever code or markup you want in it. I've also noticed that moving code across templates seems to work fine, unlike in other software. However, I haven't tested that very extensively.
3.  In the place where you want the template to be included, use the following line of code (assuming the new template is called `toolarea.inc.php`:

<!-- -->

    <?php require THEBUGGENIE_CORE_PATH . 'templates/toolarea.inc.php'; ?>

There are probably other constants similar to `THEBUGGENIE_CORE_PATH` for the other template paths, but I didn't need to look into that.

There is also a `include_template()` function that accepts a path (e.g. `'project/milestonedetailsissue'`) and an associative array of parameters.

## PHP in templates

PHP in templates is kept to a minimum, to adhere to a proper MVC-style separation. It’s only used for:

-   Conditionals (if)
-   Looping
-   Template functions (see section below for a few of those)
-   Basic PHP functions like `isset()`

The syntax for the control structures is the [alternative, longer one](http://php.net/manual/en/control-structures.alternative-syntax.php) to make them clearer, similarly to other software using PHP for templating, like Wordpress.

## Functions used in templates

These are PHP functions used inside `<?php` and `?>`.

-   `__()` prints internationalized phrases. In English it makes no difference, but in other languages, it will print out the translation of the parameter. This is how all content phrases should be printed out.
-   `make_url()` [Makes internal URLs](http://issues.thebuggenie.com/wiki/TheBugGenie%3ADevelopment%3ARouting#article_149_toc_3)
-   `link_tag()` prints out an HTML link (`<a href>`). It accepts three parameters:
    -   URL: The `href` attribute
    -   content: The link text (i.e. the content of the tag)
    -   attributes: A PHP associative array of HTML attributes
-   `image_tag()` prints out an HTML image tag (`<img>`). It accepts two parameters:
    -   URL: The `src` attribute
    -   attributes: A PHP associative array of HTML attributes
-   `javascript_link_tag()` same as link\_tag() with a URL of `"javascript:void(0)"`
