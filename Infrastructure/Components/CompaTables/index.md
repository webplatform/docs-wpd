= Summary =
A MediaWiki extension to read data from a JSON object into human readable HTML tables showing browser feature compatibility.

This page describes the use of the data we publish, 



== FAQ ==

=== What is the format of the data? ===

Here is one entry sample. The "''css''" key is what we refer to as a ''topic'', and "''border''" is what we call a ''feature''.

What generates the data is inside the "'''contents'''" section where we separate by "''mobile''" and "''desktop''".

You can safely ignore the following keys: "breadcrumb", "jsonselect", and "notes". They were created for maintenance and might be removed in a near future.

<syntaxHighlight lang="js">
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
</syntaxHighlight>


==== Support level values legend ====

Based on [https://github.com/Fyrd/caniuse/blob/master/CONTRIBUTING.md#supported-changes caniuse.com's] model:

{|
|'''y'''|(Y)es, supported by default
|-
|'''a'''|(A)lmost supported (aka Partial support)
|-
|'''n'''|(N)o support, or disabled by default
|-
|'''p'''|No support, but has (P)olyfill
|-
|'''u'''|Support ''is'' (u)nknown
|-
|'''x'''|Requires prefi(x) to work
|}


=== How do you get the compatibility tables on your docs pages? ===

We created a [[WPD:Infrastructure/Components/WebPlatformDocsExtensionBundle|MediaWiki extension "WebPlatformDocs Extension bundle"]] that takes care of generating the HTML views you see on our documentation pages. This extension reads the data from flat-file JSON file.

Each documentation page that should require a compatibility table have, in some way, an inclusion of the [http://docs.webplatform.org/wiki/Template:Compatibility Template:Compatibility "template"]. If you want to see how we set the inclusion in place, head over to  [[WPD:Projects/CompaTables/Adding_to_our_content]].

=== Can I get and use the data? ===

Sure you can!  Our compatibility table is based on a raw JSON file and you can use it too.  We serve it from [http://docs.webplatform.org/compat/data.json '''docs.webplatform.org/compat/data.json'''], and also serve an idempotent [http://docs.webplatform.org/compat/data.json "''human friendly''" ('''data-human.json''') version with indentation]. 

If you are command line inclined, you can also make queries to it using ''[https://github.com/ddopson/underscore-cli underscore-cli]''. The page [[WPD:Projects/CompaTables/Reading_the_data.json_file]] explains how to do.


=== Can I improve the data? ===

Sure!  At this time, we published our raw compatibility data as [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''' on GitHub]. The manual edition is a temporary process until we improve it.


== Also related ==
* '''Project page''':  see [[WPD:Projects/CompaTables]]