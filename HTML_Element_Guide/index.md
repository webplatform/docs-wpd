---
title: HTML Element Guide
uri: 'WPD:HTML Element Guide'

---
### Before you begin

Before you begin, you already should have:

-   taken the steps to register for this site, communicate with the team, and work with the wiki. (Select ["Editing"](/WPD:Editors_Guide) from any page on the site.)
-   ran through at least one basic contribution. (See how to [start contributing content](/WPD:Getting_Started), and cycle through one basic task, such as fixing a link or adding a summary to a page.)

### High-level steps

Below, Chris Mills runs through updating a property. But basically, you:

-   pick a property from the HTML elements list at <http://docs.webplatform.org/wiki/html/elements>. Tell us about what you want to do.
-   read the HTML element page through, if it already exists. If not, tell a steward and we will create it for you.
-   compare it to its spec(s).
-   compare the content to other reputable sites, such as Mozilla Developer Network.
-   play around with the elements documented – you can use our playground <http://code.webplatform.org>.
-   update the page based on your findings
-   remove any flags you think are no longer necessary
-   let us know you've done a page and if you'd like a review

## Choosing an element to work on

So the first step is to have a look at which properties you would like to work on. I would suggest grabbing a group of related properties that would work well as unit to work on. So for example:

-   table
-   tr
-   td
-   th

## Assigning you to work on your chosen properties

Once you have grabbed some properties to work on, let us know, so we can track who is working on what, then work through each property until you have completed your set.

## Entering data on the page

Now you are ready to start gathering the data to enter into your page. I'd advise that you gather the data and record it offline first, just in case something stupid happens and you lose your edits. I'm not saying it *will* happen, but you never know with Wikis! So copy the following headings, put them into your text editor, then read below on how to fill them in.

-   Custom page title: usually just the name of the element
-   Standardization status: what standardization stage is the element in? If it appears in multiple specs, then choose the most mature status, provided the element hasn't been massively repurposed in HTML5
-   API Name: if there is an associated API for the element, e.g. in the case of `<canvas>`
-   Article summary: provide a one line summary of what the element does. What is its purpose?
-   DOM Interface: what is the element's DOM interface?
-   Main content: provided detailed content on how the element works, what it does, use cases, attributes.
-   Examples: provide a useful working example if the element. It is best to use our codelet tool, found at <http://code.webplatform.org/>
-   Notes and usage: this is a good place to add real world examples if quirks and annoyances with using the element, along with real world solutions. This is the real valuable stuff that isn't generally picked up easily. For example, browser specific bugs, limitations in usage, comment mistakes, limitations in CSS styling on form elements. Ignore the import notes section.
-   Related specifications: list the name, URL, W3C standardization status and relevant changes for the element. The last couple of specs will do in most cases. Relevant changes is for recording anything significant that has changed about the element's purpose in that spec. For example, in HTML definition list was changed to description list. You can provide more details in the main content or usage sections above if needed.
-   Compatibility sections: ignore these. We are currently in the process of automating browser support data.
-   See also section: Provide useful links to related ref docs, tutorials, etc.

After collecting all the information, you'll then need to go through the different form fields in the edit page and fill each one in.

### Researching information

You should research the information for your article and how to verify its correct, using trustworthy sites like MDN, caniuse, quirksmode and relevant HTML specs. Review existing documentation from other sources and then read the relevant specs. If the sources all agree then you can accept the information as correct, but if they disagree you should do original research or ask for help from more knowledgeable members.

When you have finished writing a page, you should get someone else to review it to verify its quality.

### Putting information that applies to multiple elements in separate pages

NOTE: One important thing you should consider when entering information into your property pages is whether any of that information also applies to other HTML elements. If it does, then you should consider putting that information into a separate page, whether it is a concept, attribute or whatever. This way, you can save others a lot of time and repetition.

So for example, you would cover a universal attribute in its own page, and not talk about it separately on each page that covers it. For example, the `class` attribute is covered at <http://docs.webplatform.org/wiki/html/attributes/class>

If you were describing the high level usage of tables and showing a quick guide, you would probably do this in the "concepts" tree, along with, "viewport," "vendor prefixes," and "standards mode." Readers may benefit from links to tutorials on the subject available as "HTML learning material."
