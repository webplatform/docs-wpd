---
title: 'Frequently Asked Questions ("FAQ")'
uri: 'WPD:Compatibility Info/FAQ'

---
Questions we have been asked about our use of the Compatibility data and tables in our content.

## Where is the data coming from?

The data was originally polled from [Mozilla Developer Network ("MDN")](http://developer.mozilla.org) as a one time import. The data was read using an [importer we made for this purpose (code on GitHub)](https://github.com/webplatform/mdn-compat-importer). We converted into a JSON file that we used as a starting point.

At this time we are maintaining this data in [**webplatform/compatibility-data** on GitHub](https://github.com/webplatform/compatibility-data).

## The compatibility data has been changed since I maintained it in the wiki (where is it?)

When you added data to the document you are talking about, did you see the warning about our intention to not maintain compatibility data in the wiki?

You do not see the previous compatibility table based on the wiki source because we separated the way of storing the data, and how to generate the tables from the wiki content.

The compatibility data you see in [GitHub/webplatform/compatibility-data repo](https://github.com/webplatform/compatibility-data) as a big JSON file has been scraped from MDN, as a one time import, a few weeks ago.

The objective of this is to ease the maintenance of the data, and eventually, remove the need to maintain manually. Our end goal is to feed data from browser builds test runs coming from [GitHub/w3c/web-platform-test](https://github.com/w3c/web-platform-test) tests which will give us great compat data accuracy.

## What is the format of the data?

Here is one entry sample. To represent this sample we could annotate it as `feature="css" topic="border"`.

What generates the HTML table is inside "**contents**" section where we separate by "*mobile*" and "*desktop*" browser types. In each browser types, we list a sub feature description as the key. This feature description (e.g. "Basic support") is freeform text and anything can be used to describe.

You can safely ignore the "breadcrumb", "jsonselect", and "notes" keys. They were created for maintenance and might be removed in a near future.

``` js
{
  "data": {
    "css": {
      "border": {
        "breadcrumb": ["css", "border"],
        "jsonselect": ":root > .data > .css > .border",
        "contents": {
          "desktop": {
            "Basic support": {
              "Chrome": { "1.0": "y" },
              "Firefox": { "notes": { "normal": "1.0 (1.7 or earlier)" }, "1.0": "y" },
              "Internet Explorer": { "4.0": "y" },
              "Opera": { "3.5": "y" },
              "Safari": { "notes": { "normal": "1.0 (85)" }, "1.0": "y" }
            }
          },
          "mobile": {
            "Basic support": {
              "Android": { "?": "u" },
              "Firefox Mobile": { "notes": { "normal": "1.0 (1.9.2)" }, "1.0": "y" },
              "IE Phone": { "?": "u" },
              "Opera Mobile": { "?": "u" },
              "Safari Mobile": { "1.0": "y" }
            }
          }
        },
        "links": [
          {
            "title": "Original article on MDN in css border",
            "url": "https://developer.mozilla.org/en-US/docs/Web/CSS/border"
          }
        ]
      }
    }
  }
}
```

### Support level values legend

Based on [caniuse.com's](https://github.com/Fyrd/caniuse/blob/master/CONTRIBUTING.md#supported-changes) model:

||
|**y**|(Y)es, supported by default|
|**a**|(A)lmost supported (aka Partial support)|
|**n**|(N)o support, or disabled by default|
|**p**|No support, but has (P)olyfill|
|**u**|Support *is* (u)nknown|
|**x**|Requires prefi(x) to work|

## How do you get the compatibility tables on your docs pages?

We created a [MediaWiki extension "WebPlatformDocs Extension bundle"](/WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle) that takes care of generating the HTML views you see on our documentation pages. This extension reads the data from flat-file JSON file.

Each documentation page that should require a compatibility table have, in some way, an inclusion of the [Template:Compatibility "template"](http://docs.webplatform.org/wiki/Template:Compatibility). If you want to see how we set the inclusion in place, head over to [WPD:Projects/CompaTables/Adding\_to\_our\_content](/WPD:Projects/CompaTables/Adding_to_our_content).

## Can I get and use the data?

Sure you can! Our compatibility table is based on a raw JSON file and you can use it too. We serve it from [**docs.webplatform.org/compat/data.json**](http://docs.webplatform.org/compat/data.json), and also serve an idempotent ["*human friendly*" (**data-human.json**) version with indentation](http://docs.webplatform.org/compat/data.json).

If you are command line inclined, you can also make queries to it using *[underscore-cli](https://github.com/ddopson/underscore-cli)*. The page [WPD:Projects/CompaTables/Reading\_the\_data.json\_file](/WPD:Projects/CompaTables/Reading_the_data.json_file) explains how to do.

## Can I improve the data?

Sure! At this time, we published our raw compatibility data as [**webplatform/compatibility-data** on GitHub](https://github.com/webplatform/compatibility-data). The manual edition is a temporary process until we improve it.
