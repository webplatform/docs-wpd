= Reading the JSON file =

Some examples on how you can read the data using ''underscore-cli''.

== Query using the terminal ==
The compatibility data can be read either from the published location [http://docs.webplatform.org/compat/data.json docs.webplatform.org/compat/data.json] or through the [https://github.com/webplatform/compatibility-data '''webplatform/compatibility-data''' project on GitHub]. The latter provides the ''underscore-cli'' dependency out of the box.

<syntaxHighlight lang="bash">
git clone https://github.com/webplatform/compatibility-data.git
cd compatibility-data
npm install
cat data-human.json | underscore extract 'data.css.cursor'
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