---
title: WPD:Projects/CompaTables/Reading the data.json file
path: Projects/CompaTables/Reading_the_data.json_file

---
<h1><span class="mw-headline" id="Reading_the_JSON_file">Reading the JSON file</span></h1>
<p>Some examples on how you can read the data using <i>underscore-cli</i>.
</p>
<h2><span class="mw-headline" id="Query_using_the_terminal">Query using the terminal</span></h2>
<p>The compatibility data can be read either from the published location <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/data.json">docs.webplatform.org/compat/data.json</a> or through the <a rel="nofollow" class="external text" href="https://github.com/webplatform/compatibility-data"><b>webplatform/compatibility-data</b> project on GitHub</a>. The latter provides the <i>underscore-cli</i> dependency out of the box.
</p><p><br />
</p>
<pre class="language-bash" data-lang="bash">
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
</pre>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:26595-0!*!*!!*!*!*!esi=1 and timestamp 20150810200110 and revision id 70600
 -->
