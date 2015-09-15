---
title: Inspiration
tags:
  - Design
uri: 'WPD:Design/Inspiration'

---
Here are some site features from various sites that might be good inspiration for our own site design.

## <span>Adobe Web Platform Team Blog</span>

<http://blogs.adobe.com/webplatform/>

Nice body-text font, readable and friendly. [Ubuntu](http://font.ubuntu.com/) typeface with font-size of 16px and line-height of 24px.

![AdobeBlog.png](/WPD/assets/public/7/77/AdobeBlog.png)

## <span>VoilaVie.fr</span>

<http://www.voilavie.fr/view/2595>

This site has several nice features:

### <span>Shrinking Header</span>

The header banner shrinks and retracts when the user scrolls down, changing the focus from the initial impression of site identity to an unobtrusive, utilitarian

Full:

![Voilavie-full.png](/WPD/assets/public/4/47/Voilavie-full.png)

Scrolled:

![Voilavie-scrolled.png](/WPD/assets/public/0/09/Voilavie-scrolled.png)

### <span>Animated Scrolling Gallery Thumbnails</span>

Each gallery thumbnail consists of a picture and a caption; when the item is scrolled over, the caption title turns red, and the picture scrolls up to reveal the caption description.

      ![Voilavie-gallery.png](/WPD/assets/public/7/7f/Voilavie-gallery.png)![Voilavie-gallery-mouseover.png](/WPD/assets/public/a/a3/Voilavie-gallery-mouseover.png)

## <span>BadassJS</span>

<http://badassjs.com/>

A nice use of dropshadow on the content area, trendy floating folded banner, and subtle grid background to add texture.

![Badassjs.png](/WPD/assets/public/3/35/Badassjs.png)

## <span>HTML5Rocks</span>

<http://www.html5rocks.com/>

### <span>Search & Navigation</span>

Nice use of icons in full-width menu dropdown to indicate different technology categories. Also, nice layout and colors on menus.

![Html5rocks.png](/WPD/assets/public/9/97/Html5rocks.png)

Ability to filter list of articles by format, audience, technology or tags (would be nice to have other parameters, like date, author, etc.).

![Html5rocks-filters.png](/WPD/assets/public/7/76/Html5rocks-filters.png)

### <span>Profile Page / Bio</span>

Map of location, profile picture, list of contributions. (Our site should have a profile page for each contributor, but might have a "collection page" for all contributors in a team or employed by a specific organization.)

![Html5rocks-profile.png](/WPD/assets/public/4/4d/Html5rocks-profile.png)

## <span>DocHub</span>

<http://dochub.io/>

Excellent autocomplete live-filtering search box. Simple, clear, non-distracting design.

![Dochub.png](/WPD/assets/public/3/33/Dochub.png)

## <span>ReadTheDocs</span>

<http://readthedocs.org/docs/sublime-text-unofficial-documentation/en/latest/search_and_replace/search_and_replace.html>

Elided long strings on items in sidebar are revealed in full text when sidebar is moused over (or in focus), rather than using a horizontal scroll bar. Focused list item is outlined.

For serial content, it's good to have a "previous" and "next" link, with page title, though it doesn't necessarily have to be in sidebar (could be in footer, or on right side callout, or whatever).

![Readthedocs-sidebar.png](/WPD/assets/public/6/6f/Readthedocs-sidebar.png)

## <span>The Django Book</span>

<http://djangobook.com/en/2.0/chapter02/>

Comments system lets you comment on any block inline in a handy but unobtrusive way, with a marker that indicates how many comments that block has. When the marker is activated, it brings up a forum-style comment dialog.

This could be implemented even more easily and extensibly by opening an absolute-positioned iframe with a dedicated forum page; the user could then choose to go directly to the full forum view, or could comment right there. It would also be nice if the comments were in the sidebar, rather than over the content area.

  ![Djangobook-comments.png](/WPD/assets/public/5/5d/Djangobook-comments.png)![Djangobook-comments-open.png](/WPD/assets/public/a/a7/Djangobook-comments-open.png)

Some details about the comment system are on the help menu.

![Djangobook-about.png](/WPD/assets/public/e/e4/Djangobook-about.png)

## <span>Inset Code Examples</span>

I think it would be clever to have the code examples inset, as if they were "behind" the page.

![Inset-code.png](/WPD/assets/public/5/5f/Inset-code.png)

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

## <span>HTML Dog</span>

<http://htmldog.com/>

Nothing particularly notable about the design itself, but the structure and types of information is very useful for beginners.