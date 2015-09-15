---
title: Reading the JSON file
uri: 'WPD:Projects/CompaTables/Reading the data.json file'

---
Some examples on how you can read the data using *underscore-cli*.

## <span>Query using the terminal</span>

The compatibility data can be read either from the published location [docs.webplatform.org/compat/data.json](http://docs.webplatform.org/compat/data.json) or through the [**webplatform/compatibility-data** project on GitHub](https://github.com/webplatform/compatibility-data). The latter provides the *underscore-cli* dependency out of the box.

```
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
```