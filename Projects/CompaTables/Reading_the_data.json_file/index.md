
== Query using the terminal ==

=== Using underscore-cli utility ===

''NOTE'' To do this, you need NodeJS, NPM, and the Underscore-cli module and use the command line.

<syntaxHighlight lang="bash">
curl http://docs.webplatform.org/compat/data.json | underscore select ':root > .data > .css > .cursor'
[
  {
    "breadcrumb": ["css", "cursor"],
    "jsonselect": ":root > .data > .css > .cursor",
    "contents": { "desktop": { }, "mobile": { } },
    "links": [
      {
        "title": "Original article on MDN in css cursor",
        "url": "https://developer.mozilla.org/en-US/docs/Web/CSS/cursor"
      }
    ]
  }
]
</syntaxHighlight>