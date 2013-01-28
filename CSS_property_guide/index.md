{{Page_Title|CSS property reference guide}}
{{Flags}}
{{Summary_Section|This article is a guide to implementing a CSS property reference page.}}
{{Basic Page}}
We have compiled a rather large and hopefully exhaustive list of all existing CSS properties — this can be found at https://docs.google.com/spreadsheet/ccc?key=0AkRs-89PKiZpdE0xdm9Sb1ZvRW1ZRzMtWEdyU0Z4OEE#gid=0

We have assigned each property a priority level, starting from P0 and going down to P4. The highest priority is for vital, commonly-used properties that every browser supports, whereas the lowest level is for properties that are rarely-used, proprietary, have limited cross-browser support, or all of the above. We would like to start on the highest priority ones and work out way down.

==Choosing a property to work on==

So the first step is to have a look at which properties you would like to work on. I would suggest grabbing a group of related properties that would work well as unit to work on. In my example, I grabbed

* background
* background-attachment
* background-color
* background-image
* background-position
* background-repeat
* background-size
* background-clip
* background-origin

==Assigning yourself to work on your chosen properties==

Once you have grabbed some properties to work on, mark them with your name and e-mail address, in the XXXXXXXXXX column

[CHRIS - HAVE WE GOT A FACILITY FOR MARKING UP WHO IS ASSIGNED TO EACH PROPERTY?]

Then work through each property until you have completed your set. In this example I will do background-image.

==Creating your page, in the right place==

First, look for the prior existence of a page about this property on the WPD wiki. The general URL scheme is

http://docs.webplatform.org/wiki/css/properties/property-name

So this page should be placed at 

http://docs.webplatform.org/wiki/css/properties/background-image

If it already exists, great! Go on to the next step.

If not, then it is worth checking whether it exists at the wrong location. First try entering your property name in the WPD search box and see if a specific page turns up. The URL might be wrong — it might have "properties" swapped out for "Properties", or "Background-Image" swapped out for "background-image", or a forward slash on the end of the URL. These all make it a different URL, as Media Wiki has a number of quirks, including case-sensitive URLs.

If it already exists in the wrong place, we need to move it into the right place, using the "Move" tool, found in the tools menu when you are logged in. You need to enter a new slug for it to sit at. If there is something already at the new location, it will warn you and ask if you want to delete it. Please don't! We don't want to risk losing valuable content, so make sure you move the existing content somewhere else before moving your chosen content there. A good way to deal with it is to just move the old page to a location of OLD:[slug], for example OLD:background-image.

If the page does not exist at all, you need to create a new page, using the New Page creator tool at 

http://docs.webplatform.org/wiki/WPD:New_Page

You can access this by navigating to the URL where you want the page created and clicking on the new page link.

You need to use the "CSS Property" section to create a new page for your CSS property. change "css/properties/foo" to "css/properties/property-name" (in my case it would be "css/properties/background-image") and press the "Create CSS property page button"

If you are adapting/modifying an existing page, and it has the wrong template assigned to it (you'll know because the edit form won't contain the correct fields) or no template at all (you'll get no edit form when pressing "Edit", just a single textarea containing course code), then the only way to move it to the correct form type is to edit the page source to give it the right form information to use. This often isn't that simple, so either talk to a Webplatform steward for help, or just create a new page and copy the existing information across to it.

==Entering data on the page==

Now you are ready to start entering the data into the page. You'll need to go through the different form fields in the edit page and fill each one in.

NOTE: One important thing you should consider when entering information into your property pages is whether any of that information also applies to other CSS properties. If it does, then you should consider putting that information into a separate page, whether it is a concept, function or whatever. This way, you can save others a lot of time and repetition.

So, in the case of my example, url() *-gradient() functions are viable targets within the "css/functions" tree. I have created a page to cover url() at [[css/functions/url()|CSS images: url()]], and linear and radial gradients are currently intended to be covered at [[tutorials/creating_gradients_in_css|Creating gradients in CSS]].

If you were describing background colors, rather than detail how RGBA/HSLA values work, you could instead point to pages within the "css/units" (whihc doesn't exist yet). If you find yourself using any other common jargon that's hard to classify & that readers might not be familiar with, create a link within the top-level "concepts" tree, e.g., "viewport," "vendor prefixes," or "standards
mode." Readers may also benefit from links to tutorials on the subject available as "CSS learning material." (Other areas such as HTML, JavaScript, and SVG have their own learning material areas.)

===Summary information===

First of all, let's start with the summary information near the top of the page.

====Page title====

Enter the property name, for example background-image

====Brief description====

Enter a very brief description of function, for example "Applies background images to HTML elements."

====Summary====

Enter a slightly more detailed description of functionality, including some more information about usage and a link to a tutorial in case the reader is not very familiar with the property in question, and needs a really detailed walkthrough. For example:

"The background-image property allows you to apply one or more background images to an element. These can be url() paths to image files, or CSS3 linear or radial gradients. For more information, consult [[tutorials/using_css_background_images|Using CSS background images]] and [[tutorials/creating_gradients_in_css|Creating gradients in CSS]]."

====The data table====

Fill these data items in as exactly as you can.

* Initial value: none
* Computed value: n/a
* Inherited: no
* Applies to: all elements
* CSS Object Model property: backgroundImage
* Media: visual, print
* Animatable: yes
* Shorthand: background

===Syntax and values===

Now on to the syntax and value explanations

====Syntax====

You should provide a different line for all notable different value types, which are then explained in the "Values" section

for example

<pre>background-image: url(path/to/image.png) /* Use an image file as a background image */
background-image: linear-gradient(to bottom, #f00, #aaa) /* Use a CSS3 linear gradient as a background image */
background-image: radial-gradient(50% 50%, circle, #f00, #aaa) /* Use a CSS3 radial gradient as a background image */
background-image: linear-gradient(to bottom, #f00, #aaa), url(path/to/image.png), url(path/to/image2.png)  /* Apply multiple background images to the same element */</pre>

====Values====

Here, all the possible value types indicated in the syntax section should be expanded upon and explained clearly

for example

* url(path/to/image.png)
**	This value contains a path to an image that you want to apply to the element in question as a background image, using the CSS images syntax, as described at [[css/functions/url()|CSS images: url()]].
* linear-gradient(to bottom, #f00, #aaa)
** 	Programmatically creates a gradient that travels from one side of the element to the other. For more on the syntax, read [[tutorials/creating_gradients_in_css|Creating gradients in CSS]]
* radial-gradient(50% 50%, circle, #f00, #aaa)
**	Programmatically creates a gradient that radiates outwards from a specified point on the element's background. For more on the syntax, read [[tutorials/creating_gradients_in_css|Creating gradients in CSS]].
* Multiple background images		
** 	You can apply multiple background images to a single element (image files, gradients, or a mixture) by including all the image references in the property value, with each one separated by a comma. Images referenced earlier in the property value appear in front of images referenced later.

===Usage===

The usage section is meant to contain notes that impart useful, practical knowledge about using the property in the real world. What do you really need to know when trying to use this property in production?

For example

"Background images in general have good support across browsers; there are a few things to take note of, however:

* Older browsers do not support multiple background images, SVG as background images or CSS gradients, so be careful when using these options to make sure that a fallback is provided that will make content readable on older browsers, such as a simple solid colour.
* When using multiple background images, the image at the start of the comma delimited list appears on top of ones later on. This might seem contrary to how CSS is expected to behave.
* Because gradients are still supported in some browsers with prefixes and some not, and some with a slightly older syntax, you should use multiple background gradient properties with different syntaxes, as shown in the below examples."

===Compatibility table===

Fill in as many options on the compatibility table as you can. Data can be found in places such as caniuse.com, and XXXXXXXXX

====Basic background-image====

* Safari	
**	Desktop: 1.0 Mobile: 1.0 
* Chrome	
**	Desktop: 1.0 Mobile: 1.0
* Firefox	
**	Desktop: 1.0 Mobile: 1.0 
* IE	
**	Desktop: 4.0 Mobile: 6.0 
* Opera	
**	Desktop: 3.5 Mobile: 7.0
* Opera Mini	
**	Desktop: n/a Mobile: 4.0
* Android	
**	Desktop: n/a Mobile: 1.0 
* Blackberry	
**	Desktop: n/a Mobile: 3.8 
* Nokia N9
**	Desktop: n/a Mobile: 1.0 
	
====Multiple backgrounds====

* Safari	
**	Desktop: 1.0 Mobile: 1.0 
* Chrome	
**	Desktop: 1.0 Mobile: 1.0
* Firefox	
**	Desktop: 3.6 Mobile: 1.0 
* IE	
** 	Desktop: 9.0 Mobile: 8.0 
* Opera	
**	Desktop: 9.0 Mobile: 8.5
* Opera Mini	
**	Desktop: n/a Mobile: 5.0
* Android	
**	Desktop: n/a Mobile: 1.0 
* Blackberry	
**	Desktop: n/a Mobile: 3.8 
* Nokia N9
**	Desktop: n/a Mobile: 1.0 
	
====SVG background images====

* Safari	
**	Desktop: 1.0 Mobile: 1.0 
* Chrome	
**	Desktop: 8.0 Mobile: 1.0
* Firefox	
**	Desktop: 4.0 Mobile: 1.0 
* IE	
**	Desktop: 9.0 Mobile: 8.0 
* Opera	
**	Desktop: 9.5 Mobile: 10.0
* Opera Mini	
**	Desktop: n/a Mobile: 6.0
* Android	
**	Desktop: n/a Mobile: 1.0 
* Blackberry	
**	Desktop: n/a Mobile: 3.8 
* Nokia N9
**	Desktop: n/a Mobile: 1.0
	
====Gradients====

* Safari	
**	Desktop: 1.0 with -webkit- Mobile: 1.0 with -webkit- 
* Chrome	
**	Desktop: 1.0 with -webkit- Mobile: 1.0 wit -webkit-
* Firefox	
**	Desktop: 4.0 with -moz- Mobile: 1.0 
* IE	
**	Desktop: 10 without prefix Mobile: 8.0 
* Opera	
**	Desktop: 11 with -o-, 12.5 without prefix Mobile: 11.0 with -o-, 12 without prefix
* Opera Mini	
**	Desktop: n/a Mobile: no
* Android	
**	Desktop: n/a Mobile: 1.0 
** Blackberry	
*	Desktop: n/a Mobile: 3.8 
** Nokia N9
*	Desktop: n/a Mobile: 1.0


===Compatibility notes===

* IE < 9: doesn't support SVG for background-images, or multiple background images, or gradients
* IE < 10: doesn't support gradients
* Not all browsers support animation of background images. Recent -webkit- based browsers transition between background images by cross fading.

===Examples===

For the examples section, you should provide one or two brief examples that succinctly show how to do a real world implementation of the property being shown. Just a brief CSS snippet will suffice for the printed example; for the embedded real working example, you'll need to provide full HTML too.

<pre>.one {
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
}</pre>

===Interactive examples===

At a slightly later date, we are intending to integrate [[http://dabblet.com/ Dabblet]] with our site, so we will be able to have live examples running inside our references and tutorials. Until the live example viewer is properly implemented, I would suggest doing one of the following with your complete examples:

# Including all the source code for the examples inside <code>&lt;pre&gt;</code> elements in the property page
# Uploading the example(s) to [[http://www.github.com Github]], [[https://help.github.com/articles/creating-project-pages-manually creating a project page]] for each one, and then linking to those from the property page. This is a good idea as it means that we can show an example running live and accept pull requests from others to help fix bugs and improve examples.

For example, I have put my background-image example at

https://github.com/chrisdavidmills/background-image

And created a project page that can be viewed at

http://chrisdavidmills.github.com/background-image/background-image.html

===Related articles===

For the related articles, you should a include a wide variety of resources that nicely complement the subject in hand. You should choose:

* Other reference articles covering properties (and subjects) related to this one
* Tutorial articles that show how to use the property in more detail
* Articles that contain interesting discussions related to the property, which might be of controversial or otherwise interesting nature
* links to the spec(s) that the property appears in

Here's some examples for the background-image example:

====Tutorials====

* [[tutorials/using_css_background_images|Using CSS background images]]
* [[tutorials/creating_gradients_in_css|Creating gradients in CSS]]

====Useful external articles====

* [[http://www.netmagazine.com/tutorials/get-grips-css3-multiple-background-images Get to grips with CSS3 multiple background images]], by Prisca Schmarsow

====Specs====

* [[http://www.w3.org/TR/css3-background/ CSS Backgrounds and Borders Module Level 3]]
* [[http://www.w3.org/TR/CSS21/colors CSS2.1 Colors and Backgrounds]]
{{Notes_Section}}
{{Topics|CSS}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}