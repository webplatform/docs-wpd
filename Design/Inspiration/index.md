---
title: 'Inspiration'
tags:
  - Design
uri: 'WPD:Design/Inspiration'

---
Here are some site features from various sites that might be good inspiration for our own site design.

## Adobe Web Platform Team Blog

<http://blogs.adobe.com/webplatform/>

Nice body-text font, readable and friendly. [Ubuntu](http://font.ubuntu.com/) typeface with font-size of 16px and line-height of 24px.

![AdobeBlog.png](//static.webplatform.org/7/77/AdobeBlog.png)

## VoilaVie.fr

<http://www.voilavie.fr/view/2595>

This site has several nice features:

### Shrinking Header

The header banner shrinks and retracts when the user scrolls down, changing the focus from the initial impression of site identity to an unobtrusive, utilitarian

Full:

![Voilavie-full.png](//static.webplatform.org/4/47/Voilavie-full.png)

Scrolled:

![Voilavie-scrolled.png](//static.webplatform.org/0/09/Voilavie-scrolled.png)

### Animated Scrolling Gallery Thumbnails

Each gallery thumbnail consists of a picture and a caption; when the item is scrolled over, the caption title turns red, and the picture scrolls up to reveal the caption description.

      ![Voilavie-gallery.png](//static.webplatform.org/7/7f/Voilavie-gallery.png)![Voilavie-gallery-mouseover.png](//static.webplatform.org/a/a3/Voilavie-gallery-mouseover.png)

## BadassJS

<http://badassjs.com/>

A nice use of dropshadow on the content area, trendy floating folded banner, and subtle grid background to add texture.

![Badassjs.png](//static.webplatform.org/3/35/Badassjs.png)

## HTML5Rocks

<http://www.html5rocks.com/>

### Search & Navigation

Nice use of icons in full-width menu dropdown to indicate different technology categories. Also, nice layout and colors on menus.

![Html5rocks.png](//static.webplatform.org/9/97/Html5rocks.png)

Ability to filter list of articles by format, audience, technology or tags (would be nice to have other parameters, like date, author, etc.).

![Html5rocks-filters.png](//static.webplatform.org/7/76/Html5rocks-filters.png)

### Profile Page / Bio

Map of location, profile picture, list of contributions. (Our site should have a profile page for each contributor, but might have a "collection page" for all contributors in a team or employed by a specific organization.)

![Html5rocks-profile.png](//static.webplatform.org/4/4d/Html5rocks-profile.png)

## DocHub

<http://dochub.io/>

Excellent autocomplete live-filtering search box. Simple, clear, non-distracting design.

![Dochub.png](//static.webplatform.org/3/33/Dochub.png)

## ReadTheDocs

<http://readthedocs.org/docs/sublime-text-unofficial-documentation/en/latest/search_and_replace/search_and_replace.html>

Elided long strings on items in sidebar are revealed in full text when sidebar is moused over (or in focus), rather than using a horizontal scroll bar. Focused list item is outlined.

For serial content, it's good to have a "previous" and "next" link, with page title, though it doesn't necessarily have to be in sidebar (could be in footer, or on right side callout, or whatever).

![Readthedocs-sidebar.png](//static.webplatform.org/6/6f/Readthedocs-sidebar.png)

## The Django Book

<http://djangobook.com/en/2.0/chapter02/>

Comments system lets you comment on any block inline in a handy but unobtrusive way, with a marker that indicates how many comments that block has. When the marker is activated, it brings up a forum-style comment dialog.

This could be implemented even more easily and extensibly by opening an absolute-positioned iframe with a dedicated forum page; the user could then choose to go directly to the full forum view, or could comment right there. It would also be nice if the comments were in the sidebar, rather than over the content area.

  ![Djangobook-comments.png](//static.webplatform.org/5/5d/Djangobook-comments.png)![Djangobook-comments-open.png](//static.webplatform.org/a/a7/Djangobook-comments-open.png)

Some details about the comment system are on the help menu.

![Djangobook-about.png](//static.webplatform.org/e/e4/Djangobook-about.png)

## Inset Code Examples

I think it would be clever to have the code examples inset, as if they were "behind" the page.

![Inset-code.png](//static.webplatform.org/5/5f/Inset-code.png)

    <style class="example">
       style.example {
           display: inline-block;
           white-space: pre-wrap;
           border-radius: 8px;
           font-family: Monaco,Courier,MonoSpace;
           background: none repeat scroll 0 0 #777777;
           font-size: 12px;
           line-height: 1.8;
           margin: 0 0 25px;
           overflow: auto;
           padding: 10px 20px 10px 10px;
           position: relative;
           box-shadow: 0 0 25px #000000 inset;
           color: white;
       }
    </style>

## HTML Dog

<http://htmldog.com/>

Nothing particularly notable about the design itself, but the structure and types of information is very useful for beginners.
