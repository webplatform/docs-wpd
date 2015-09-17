---
title: 'CSS property editing guide'
summary: 'Help us update, review, add samples, and add quality to the CSS properties! This article is a guide to implementing a CSS property reference page.'
tags:
  - Basic
  - Pages
  - CSS
uri: 'WPD:CSS property guide'

---
## Summary

Help us update, review, add samples, and add quality to the CSS properties! This article is a guide to implementing a CSS property reference page.

### Before you begin

Before you begin, you already should have:

-   taken the steps to register for this site, communicate with the team, and work with the wiki. (Select ["Editing"](/WPD:Editors_Guide) from any page on the site.)
-   ran through at least one basic contribution. (See how to [start contributing content](/WPD:Getting_Started), and cycle through one basic task, such as fixing a link or adding a summary to a page.)

### High-level steps

Below, Chris Mills runs through updating a property. But basically, you:

-   pick a property (preferably one that's priority-0 through priority-2) from [the weekly list](/Meta:web_platform_wednesday) and have a coordinator add your name in the owner/reviewer column
-   read the CSS property page through
-   compare it to its spec(s)
-   compare the content to other reputable sites, such as Mozilla Developer Network
-   play around with the elements documented – you can use our playground <http://code.webplatform.org>.
-   update the page based on your findings
-   remove any flags you think are no longer necessary
-   ask a coordinator to update the [the weekly list](/Meta:web_platform_wednesday) with your status
-   send us a message @webplatform to let us know you've done a page and if you'd like a review

## Ignore the master CSS properties spreadsheet

We have compiled a rather large and hopefully exhaustive list of all existing CSS properties — this can be found at [the master list](/Meta:web_platform_wednesday/master_list) - but you can ignore this.

We have assigned each property a priority level, starting from Priority-0 and going down to Priority-4, where P0 is the highest priority for vital, commonly-used properties that every browser supports. P4, then, is considered the lowest level is for properties, because they're rarely-used, proprietary, have limited cross-browser support, or all of the above. We would like to start on the highest priority ones and work out way down.

## Choosing a property to work on

So the first step is to have a look at which properties you would like to work on. I would suggest grabbing a group of related properties that would work well as unit to work on. So for example, I grabbed

-   background
-   background-attachment
-   background-color
-   background-image
-   background-position
-   background-repeat
-   background-size
-   background-clip
-   background-origin

## Assigning you to work on your chosen properties

Once you have grabbed some properties to work on, let us know, so we can track who is working on what: Have a coordinator add your name into [the weekly list](/Meta:web_platform_wednesday) Then work through each property until you have completed your set. In this example I will do background-image — see my finished example at <http://docs.webplatform.org/wiki/css/properties/background-image>

## Creating your page, in the right place

First, look for the prior existence of a page about this property on the WPD wiki. The general URL scheme is

<http://docs.webplatform.org/wiki/css/properties/property-name>

So this page should be placed at

<http://docs.webplatform.org/wiki/css/properties/background-image>

If it already exists, great! Go on to the next step.

If not, then it is worth checking whether it exists at the wrong location. First try entering your property name in the WPD search box and see if a specific page turns up. The URL might be wrong — it might have "properties" swapped out for "Properties", or "Background-Image" swapped out for "background-image", or a forward slash on the end of the URL. These all make it a different URL, as Media Wiki has a number of quirks, including case-sensitive URLs.

If it already exists in the wrong place, we need to move it into the right place, using the "Move" tool, found in the tools menu when you are logged in. You need to enter a new slug for it to sit at. If there is something already at the new location, it will warn you and ask if you want to delete it. Please don't! We don't want to risk losing valuable content, so make sure you move the existing content somewhere else before moving your chosen content there. A good way to deal with it is to just move the old page to a location of OLD:[slug], for example OLD:background-image.

If the page does not exist at all, you need to create a new page, using the New Page creator tool at

<http://docs.webplatform.org/wiki/WPD:New_Page>

You can access this by navigating to the URL where you want the page created and clicking on the new page link.

You need to use the "CSS Property" section to create a new page for your CSS property. change "css/properties/foo" to "css/properties/property-name" (in my case it would be "css/properties/background-image") and press the "Create CSS property page button"

If you are adapting/modifying an existing page, and it has the wrong template assigned to it (you'll know because the edit form won't contain the correct fields) or no template at all (you'll get no edit form when pressing "Edit", just a single textarea containing course code), then the only way to move it to the correct form type is to edit the page source to give it the right form information to use. This often isn't that simple, so either talk to a Webplatform steward for help, or just create a new page and copy the existing information across to it.

## Entering data on the page

Now you are ready to start gathering the data to enter into your page. I'd advise that you gather the data and record it offline first, just in case something stupid happens and you lose your edits. I'm not saying it *will* happen, but you never know with Wikis! So copy the following headings, put them into your text editor, then read below on how to fill them in.

-   Custom page title
-   Article summary
-   Data table

<!-- -->

    Initial value:
    Computed value:
    Inherited:
    Applies to:
    CSS Object Model property:
    Media:
    Animatable:
    Shorthand: (this currently doesn't exist in the CSS property form template but will be added soon. Note the related shorthand property, if one exists, in the notes section for now)

-   Syntax
-   Examples
-   Usage
-   Related specifications
-   Related articles
-   Compatibility table (You can ignore these for now. We're working on brining in the data manually.)
-   Compatibility notes (Only add something if you think it's unique and isn't represented on sites like caniuse.com or developer.mozilla.org)

After collecting all the information, you'll then need to go through the different form fields in the edit page and fill each one in.

### Researching information

You should research the information for your article and how to verify its correct, using trustworthy sites like MDN, caniuse, quirksmode and relevant CSS specs. Review existing documentation from other sources and then read the relevant specs. If the sources all agree then you can accept the information as correct, but if they disagree you should do original research or ask for help from more knowledgeable members.

When you have finished writing a page, you should get someone else to review it to verify its quality.

### Putting information that applies to multiple properties in separate pages

NOTE: One important thing you should consider when entering information into your property pages is whether any of that information also applies to other CSS properties. If it does, then you should consider putting that information into a separate page, whether it is a concept, function or whatever. This way, you can save others a lot of time and repetition.

So, in the case of my example, url() and \*-gradient() functions are viable targets within the "css/functions" tree. I have created a page to cover url() at [CSS images: url()](/css/functions/url()), and linear and radial gradients are currently intended to be covered at [Creating gradients in CSS](/tutorials/creating_gradients_in_css).

If you were describing background colors, rather than detail how RGBA/HSLA values work, you could instead point to pages within the "css/units" (whihc doesn't exist yet). If you find yourself using any other common jargon that's hard to classify & that readers might not be familiar with, create a link within the top-level "concepts" tree, e.g., "viewport," "vendor prefixes," or "standards mode." Readers may also benefit from links to tutorials on the subject available as "CSS learning material." (Other areas such as HTML, JavaScript, and SVG have their own learning material areas.)

### Summary information

First of all, let's start with the summary information near the top of the page.

#### Custom page title

Enter the property name, for example background-image

#### Top level summary

Enter a very brief description of function, for example

"The background-image property allows you to apply one or more background images to an element. These can be url() paths to image files, or CSS3 linear or radial gradients. For more information, consult [Using CSS background images](/tutorials/using_css_background_images) and [Creating gradients in CSS](/tutorials/creating_gradients_in_css)."

#### The data table

This refers to the small fields below the Summary. Fill these data items in as exactly as you can.

-   Initial value: none
-   Computed value: As specified, but with URIs made absolute
-   Inherited: no
-   Applies to: all elements
-   CSS Object Model property: backgroundImage
-   Media: visual for now (you can't currently specify more than one)
-   Animatable: yes
-   Shorthand: background
-   Percentages (ignore this)

NOTE: computed values and initial values can often be hard to find by searching on your favorite search engine. A better way to find them out is often to create a very quick test (or even just go to an already-existing web page) and play with different values of said property, and see what the computed values are reported as (most browser dev tools, e.g. Opera Dragonfly, Chrome Dev Tools, report computed values.) Sometimes the computed values are not quite as simple as you'd think. For example with the color property, the computed value is always the hexadecimal equivalent, except in the case of translucent colours, where it is always the RGBa equivalent.

Note: To check whether you property is animatable or not, write a simple test, or check out a list such as [CSS animatable properties](http://oli.jp/2010/css-animatable-properties/) by Oli Studholme.

### Syntax and values

Now on to the syntax and value explanations.

You should provide a different syntax value all notable different value types, along with a nice detailed explanation, in the **Values** form fields. These values are then used to auto-populate the **Syntax** and **Values** sections of the page.

Here, all the possible value types indicated in the syntax section should be expanded upon and explained clearly

for example

-   url(path/to/image.png)
    -   This value contains a path to an image that you want to apply to the element in question as a background image, using the CSS images syntax, as described at [CSS images: url()](/css/functions/url()).
-   linear-gradient(to bottom, \#f00, \#aaa)
    -   Programmatically creates a gradient that travels from one side of the element to the other. For more on the syntax, read [Creating gradients in CSS](/tutorials/creating_gradients_in_css)
-   radial-gradient(50% 50%, circle, \#f00, \#aaa)
    -   Programmatically creates a gradient that radiates outwards from a specified point on the element's background. For more on the syntax, read [Creating gradients in CSS](/tutorials/creating_gradients_in_css).
-   url(path/to/image.png), url(path/to/image2.png), url(path/to/image3.png)
    -   You can apply multiple background images to a single element (image files, gradients, or a mixture) by including all the image references in the property value, with each one separated by a comma. Images referenced earlier in the property value appear in front of images referenced later.

### Examples

For the examples section, you should provide one or two brief examples that succinctly show how to do a real world implementation of the property being shown. You should show your HTML and CSS, and anything else relevant, in separate sections, as provided by the edit page.

For example:

HTML

    <!DOCTYPE HTML>
    <html lang="en-US">
    <head>
        <meta charset="UTF-8">
        <title>Background-image example</title>
        <link href="background-image.css" type="text/css" rel="stylesheet">
    </head>
    <body>

    <div class="one">One</div>
    <div class="two">Two</div>
    <div class="three">Three</div>

    </body>
    </html>

CSS

    .one {
      background-image: url(images/icon.png);
      /* here we are applying a single background image to our first block level container element */
      /* (could be anything, but it is a <div>in the live example. */
    }

    .two {
      background-image: -webkit-linear-gradient(top,#aaa,#eee);
      background-image: -moz-linear-gradient(top,#aaa,#eee);
      background-image: -ms-linear-gradient(top,#aaa,#eee);
      background-image: -o-linear-gradient(top,#aaa,#eee);
      background-image: linear-gradient(to bottom,#aaa,#eee);
      /* Here we are applying a linear gradient to our second block level container. */
      /* We have included a line with each different vendor prefix type, so that all supporting */
      /* browsers will have something they can apply. This includes a prefixless version of the */
      /* property, which uses the latest version of the syntax for the spec. As browsers update their  */
      /* implementations and drop their prefixes, tyhey can start to use this syntax instead, meaning */
      /* that the code will still work. */
    }

    .three {
      background-image: url(images/icon.png), -webkit-linear-gradient(top,#aaa,#eee);
      background-image: url(images/icon.png), -moz-linear-gradient(top,#aaa,#eee);
      background-image: url(images/icon.png), -ms-linear-gradient(top,#aaa,#eee);
      background-image: url(images/icon.png), -o-linear-gradient(top,#aaa,#eee);
      background-image: url(images/icon.png), linear-gradient(to bottom,#aaa,#eee);
      /* In this case we are applying both the background image and the gradient to our third block level container. */
    }

#### Live examples

At a slightly later date, we are intending to integrate [Dabblet](http://dabblet.com/) with our site, so we will be able to have live examples running inside our references and tutorials. Until the live example viewer is properly implemented, we would suggest just showing the source code in the page for now, as instructed above. In my finished example page, I have hosted a live example at Github; feel free to host a live version at Github or another place if you feel like it.

### Usage (optional)

The Usage section should contain notes that impart useful, practical knowledge about using the property in the real world. What do you really need to know when trying to use this property in production?

For example

"Background images in general have good support across browsers; there are a few things to take note of, however:

-   Older browsers do not support multiple background images, SVG as background images or CSS gradients, so be careful when using these options to make sure that a fallback is provided that will make content readable on older browsers, such as a simple solid colour.
-   When using multiple background images, the image at the start of the comma delimited list appears on top of ones later on. This might seem contrary to how CSS is expected to behave.
-   Because gradients are still supported in some browsers with prefixes and some not, and some with a slightly older syntax, you should use multiple background gradient properties with different syntaxes, as shown in the below examples."

### Related specifications

enter the most current specification the property is included in, AND the recommendation the property was included in, in the case of old properties that were included in CSS 1, 2.1, etc.

For example:

Name: CSS 2.1 URL: <http://www.w3.org/TR/CSS21/colors> Status: W3C Recommendation Relevant changes:

Name: CSS Backgrounds and Borders Module Level 3 URL: <http://www.w3.org/TR/css3-background/> Status: W3C Candidate Recommendation Relevant changes: Multiple background images can be specified on the same element.

### Compatibility table

You can ignore the compatibility table for now. (We're working on brining in the data manually.) Update the compatibility notes field only if you think it's unique and isn't represented on sites like caniuse.com or developer.mozilla.org.

### Compatibility notes

Use the compatibility notes section to enter any useful specifics you have relating to browser compatibility. For example:

-   IE \< 9: doesn't support SVG for background-images, or multiple background images, or gradients
-   IE \< 10: doesn't support gradients
-   Not all browsers support animation of background images. Recent -webkit- based browsers transition between background images by cross fading.

### Related articles

For the related articles, you should a include a wide variety of resources that nicely complement the subject in hand. You should choose:

-   Other reference articles covering properties (and subjects) related to this one
-   Tutorial articles that show how to use the property in more detail
-   Articles that contain interesting discussions related to the property, which might be of controversial or otherwise interesting nature
-   links to the spec(s) that the property appears in

Here's some examples for the background-image example:

#### Internal pages (put in the *manual links'* section)

-   [Using CSS background images](/tutorials/using_css_background_images)
-   [Creating gradients in CSS](/tutorials/creating_gradients_in_css)

#### Useful external articles (put in the **external links** section)

-   [Get to grips with CSS3 multiple background images](http://www.netmagazine.com/tutorials/get-grips-css3-multiple-background-images), by Prisca Schmarsow

### Anything else (put in the **Manual sections** section)=

-   x
-   y
-   z

### External attribution

Some of the existing pages will have content that comes from an external source. We are quite happy to overwrite/replace this information, to improve it, make it more consistent, and get rid of any licensing constraints that using that material brought with it. If there is external attribution specified, and you've just rewritten the page data. uncheck the external attribution options.
