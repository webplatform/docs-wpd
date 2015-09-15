---
title: Importing data into MediaWiki
uri: 'WPD:Infrastructure/procedures/Importing data into MediaWiki'

---
## <span>Summary</span>

*This documentation was initially created by Yaron Koren on August 12, 2012. Feel free to write me with any questions about it, at yaron57@gmail.com.*

Importing content into the wiki involves several steps. For each page to be imported, you need to:

1.  scrape the HTML/XML content of that page
2.  create wikitext to hold that information
3.  figure out the name for the corresponding page in the wiki
4.  save the wikitext to the wiki page of that name.

All of this assumes that there's a one-to-one correspondence between the source documents and pages in the wiki, which is not necessarily true: there could be source HTML pages that need to get split up into multiple wiki pages, or multiple HTML pages that need to get combined into one wiki page (this seems less likely), or even more complex combinations. And there could be HTML pages in more than set of documentation corresponding to the same concept - the data from these multiple sources would need to be synthesized in some way; or at the very least you would need to choose which data to use. This documentation won't explain how to do any of that, but this sort of action would essentially have to be done between steps 1 and 2 in the code.

## <span>Scraping contents</span>

There is nothing MediaWiki-specific about this step; you just need to create code that gets the relevant data from each page in a reliable way. There are many libraries that can help with HTML and XML parsing.

## <span>Wikitext</span>

Every page in MediaWiki is defined by its source text, which is in a syntax called "wikitext" (though it's generic-sounding, the name "wikitext" is only used for MediaWiki's syntax). You can view the wikitext for any page by clicking on the tab that's labeled either "Edit" or "View source", depending on whether you're allowed to edit it.

In the WebPlatform wiki, every page is meant to have the same basic structure: one or more template calls at the top, and then sections (if any) for the rest of the page. Here are the contents of the page "css/properties/font-size" (which you can also see [here](http://webplatform.org/d/index.php?title=css/properties/font-size&action=edit)):

    {{Flags
    |High-level issues=Stub
    |Content=Outdated, Incomplete, Needs Best Practices
    |Compatibility=Missing
    |Examples=Examples have errors
    }}
    {{CSS Property
    |Initial value=medium
    |Applies to=all elements
    |Inherited=Yes
    |Media=visual
    |Computed value=absolute length
    |Animatable=No
    |Values={{CSS Property Value
    |Data Type=xx-small, x-small, small, medium, large, x-large, xx-large
    |Description=A set of absolute size keywords based on the user's default font size (which is medium). Similar to presentational HTML's <font size="1"> through <font size="7"> where the user's default font size is <font size="3">.
    }}{{CSS Property Value
    |Data Type=larger, smaller
    |Description=Larger or smaller than the parent element's font size, by roughly the ratio used to separate the absolute size keywords above.
    }}{{CSS Property Value
    |Data Type=length
    |Description=A positive length. When the units are specified in em or ex,  the size is defined relative to the size of the font on the parent element of the element in question. For example, 0.5em is half the font size of the parent of the current element.
    }}{{CSS Property Value
    |Data Type=percentage
    |Description=A positive percentage of the parent element's font size.
    }}
    |Syntax=font-size: xx-small
    |Value_Name=percentage
    }}

There are no sections on this page; just calls to templates. There are two main templates on this page: "Flags" and "CSS Property". The "Flags" template is here at this point mostly still as a test, so it can safely be ignored at this point. The "CSS Property" template is the important one, holding the real content for the page. Hopefully the basic syntax of template calls makes sense from this example - it takes in a set of parameters, which can be passed in any order. Each parameter is of the form "|*field name*=*value*".

Interestingly, you can see that the "Values" parameter of this template is itself taking in a set of calls to the template "CSS Property Value". This is how "two-dimensional" data will be handled in this wiki - data that's essentially a table, instead of a single value. Any such table of data should be structured as a series of calls to the same template (one for each row), which are in turn all one value for a parameter in the larger template.

There should only ever be two dimensions at most in a page - not three or more. In other words, a template call can contain calls to other templates, but those template calls should not contain any additional calls.

What if you're trying to import data of a type that doesn't have an example on the wiki? Don't worry too much about this - feel free to come up with arbitrary names for the templates, and parameters for those templates, to store on the page. Even if there's a problem with one or more of those fields, or the names get changed later on, you will still have done 90% of the work needed for the import.

(Please don't worry about actually creating or modifying the templates in question, unless you think it will be useful for the import. It's alright if the page itself, when viewed, looks nonsensical - the key is for the wikitext to be correct.)

### <span>Sections</span>

And what about sections? They're ideal for semi-structured content that differs from page to page. For instance, if there's some page where you want to have some content specific to memory leaks, but it's only relevant to that one page, then it probably doesn't make sense to create a template parameter for it. Instead, you should have a section called "Memory leaks" in the page, under the template call(s). Section headers are defined by putting "==" around the header text. So here is how such a section could look:

    ==Memory leaks==
    Calling this function has been know to generate memory leaks when...

## <span>Page naming</span>

Page names on the WebPlatform wiki are all lowercase, and they're of the form "*language, API or framework*/*type of entity*/*name of entity*". "css/properties/font-size" is one example, obviously, while another could be "jquery/methods/append". The full naming system for this wiki has not been fully established, as far as I know - hopefully it is something that will for the most part fall into place during the import process.

## <span>Saving the page</span>

Saving the wiki page is actually possibly the easiest part of the process. MediaWiki has a URL-based (i.e. RESTful) API that can be used to perform a lot of actions, including saving pages. You can see a listing and explanation of the API [here](http://webplatform.org/d/api.php). The API is built around "actions", and the two important actions in this case are "action=login" and "action=edit". In order to save a page, you need to first call the "login" action, then the "edit" action.

The API can either be accessed directly via the URLs, or using a library that serves as a wrapper around the API. The latter is probably easier to do, though you do have to install the library (which is usually not that hard to do). There are libraries available for a large number of programming languages; you can see a fairly complete list [" here](http://en.wikipedia.org/wiki/Wikipedia:Creating_a_bot#Programming_languages_and_libraries). Some of these are Wikipedia-specific; you should only use libraries that are generic to any MediaWiki installation.

If you want to access the API URLs directly, you can do that; the API page ([here it is again](http://webplatform.org/d/api.php)) gives examples for the "login" and "edit" actions, and there's a full explanation of the MediaWiki API [here](http://www.mediawiki.org/wiki/API:Main_page).