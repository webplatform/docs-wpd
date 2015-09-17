---
title: 'Topic Pages'
uri: 'WPD:Content/Topic Pages'

---
We have a number of landing pages implied by the [WPD:Architecture](/WPD:Architecture). Most of them are captured in this migration tracking spreadsheet: <https://docs.google.com/a/chromium.org/spreadsheet/ccc?key=0AkRs-89PKiZpdHBqN2poNnJjV1c0N1FCYlN3ZUtpZ3c#gid=34>

This page documents how to go about creating them.

The primary goal of these topic pages is to make sure that users (and search engines!) know about all of the content we have within the site. The secondary goal is to explain the concepts that unite them.

**For each page, make sure to use the Basic\_Page type, and fill in the summary**. The summary will be used in other listing pages.

There are a few types of pages:

## Manually generated

Some pages are so specialized (and so little work to generate, and so unlikely to change) that it just makes sense for us to list them by hand. The main page is a good example--it needs to point to the major topic areas but those are few in number and change rarely.

The disadvantage is that if we generate them by hand they can get stale easily, so don't fall back to this unless you have to.

## Simple Sub-Directory

If all you need to do is list all of the sub-directories, MediaWiki has some built in features.

The following snippet will print out all descendants of the given URL:

    {{Special:PrefixIndex/WPD:Example_Pages/}}

Where "/WPD:Example\_Pages/" is the prefix of the URL to list the descendants of. However, this has a **crucial limitation**: it automatically prints out all *descendants*, where often all you want is the *children*.

We installed the SubPageList extension to help with this.

The code snippet you'll probably use most often is this:

``` html
<splist />
```

 The first parameter is omitted because it's the URL to list sub-pages of, and if you omit it it defaults to the current page.

You can read more at <http://www.mediawiki.org/wiki/Extension:SubPageList> .

## Query-generated

Sometimes you need to do something that's not just the descendants or children of the given page. For that you'll want to use Semantic Media Wiki's query functionality.

I've set up a template that makes this easy: [Template:API\_Listing](/Template:API_Listing) . This template accepts a query string, and abstracts away the other arcana of producing the right listing.

The query string is how you select which pages to show. Common ones would be based on the category they're in, like [[Category:CSS\_Properties]]. You can chain them together to AND them, or even do ORs. You can also filter based on semantic media properties set on them.

See <http://semantic-mediawiki.org/wiki/Help:Selecting_pages> for more information about all of the stuff you can pass to the query parameter.

## Notes from Chris

These are some notes I have recorded, from my experiences with trying to create these pages. Hopefully they will help others.

1.  First, you need to make sure your landing pages fit with the structure defined in the [WPD:Architecture](/WPD:Architecture) page. So for example I created a top level landing page for concepts by using entering "concepts" into the Basic page form at [WPD:New\_Page](/WPD:New_Page). This created [concepts](/concepts).

2.  Unfortunately I found that the concepts page had already been created, and it hadn't been created using a form. If you find this, you'll need to edit the source of the page to put the Basic page form into it, before you can then edit it and fill it in using the form. This code looks like so — copy this all and put it into the edit form, then save:

        {{Page_Title}}
        {{Flags}}
        {{Summary_Section|SUMMARY GOES HERE}}
        {{Basic_Page
        |Content=PAGE CONTENT GOES HERE
        }}
        {{Compatibility_Section
        |Not_required=Yes
        |Desktop_rows=
        |Mobile_rows=
        |Notes_rows=
        }}
        {{See_Also_Section}}
        {{Topics}}
        {{External_Attribution
        |Is_CC-BY-SA=No
        |MDN_link=
        |MSDN_link=
        |HTML5Rocks_link=
        }}

    You probably don't need most of this, but I added it all in just to be on the safe side.

3.  Now edit the page by choosing Edit, not the Edit Source option: you'll be able to edit the page using the nice form, which is necessary, and makes things a lot easier.

4.  When you create article links, often the raw relative URL fragments don't look very good, for example [concepts/Internet and Web/How does the Internet Work](/concepts/Internet_and_Web/How_does_the_Internet_Work). It is much better to use different display text in such cases, and this can be added after a pipe character, after the URL fragment. So for example:

        [[concepts/Internet and Web/How does the Internet Work|How does the Internet Work?]]

    Creates this: [How does the Internet Work?](/concepts/Internet_and_Web/How_does_the_Internet_Work)

Whatever way of populating the page you choose, make sure the TOC is easy to follow and makes sense. I did the concepts page manually, because I found that just generating the article list automatically didn't give enough control, and it didn't look very good either. For example, to list all the concept pages I used this:

    {{Special:PrefixIndex/concepts/}}

It's a good tool for making sure that you don't miss any pages of a given topic, but I wouldn't recommend it for final presentation. Have we got some kind of tool to alert us to new pages being created, so we can make sure to add them to the landing pages?
