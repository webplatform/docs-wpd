---
title: 0415 raw mtg notes
uri: 'WPD:Community/Meetings/General/2014/0415 raw mtg notes'

---
## Topic: Compat tables

renoirb: We have something working that use compatibility data from MDN

… we cannot get all the data, more on this later, but we have enough to allow the community to use it already

… you can see how it works from the [test wiki](http://docs.webplatform.org/test/) and you can see many examples in the [/test/Tests/Compatibility\_table\_and\_caching page](http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching).

… Adding a table requires to use `<compatability feature="analyser-node" format="table"></compatability>` tag.

… figuring out which key to put in `feature=""` can be found from a human-friendly JSON file at [compat/compat-mdn-human.json](http://docs.webplatform.org/compat/compat-mdn-human.json), it is a reformatted version from the raw [compat/compat-mdn.json file](http://docs.webplatform.org/compat/compat-mdn.json)

… The project had many iterations:

… 1. First iteration (led by Shepazu) was about generating HTML table based on JSON data file. The table was regenerated at every page render. If a visitor is logged in Mediawiki, it would regenerate at every page view (!)

… 2. Second iteration (led by Aaron, a reference of Ryan Lane) was about leveraging Varnish's ESI tags that allows us to freeze snippets of HTML in a page. It went well, but it isn't deployed due to limitations with our Varnish provider (Fastly). It is using a version of Varnish that cannot GZIP content AND do ESI includes. At that point, we decided to focus on importing data

… 3. Third iteration (led by Frozenice) was to create a nodejs crawler to copy and normalize the data.

… 4. Most recent iteration (led by renoirb) was to work on normalizing

… the data and add continue improving the code. It now uses internally memcached to keep the generated HTML and will serve that version until the cache is invalidated.

… The cache can be invalidated if the original JSON file is updated, or if it has been purged or if the lifetime of the cached version comes.

… That way, regardless of whether Varnish provides us the ESI version, it adds one more performance improvement before hitting our servers

… So, at the moment, we: have MDN data, can normalize it, do generate HTML tables, do have two layers of caching, have ways for users to embed the data in our wiki (!).

## Topic: Compat tables; known limitation

renoirb: As I said, we have a known limitation. … Our current implementation was already making a copy, but with a specific tool, we can concentrate [mdn-compat-importer](https://github.com/webplatform/mdn-compat-importer) only for normalizing the data

… what we are basically doing is crawling the pages, keeping a local copy as HTML to JavaScript object in files

… the normalization is basically a second-pass, , is about

… normalize what we think makes sense following Can I use's result

… We move what we are unsure in notes or removing notes, for example, if it's mozilla-specific

 renoirb: we have something working that creates a local copy of pages that has compatibility data

… the scraping is not complete due to a known issue but it is a good starting point

… eventually we will need to be aple to scrape everythin. But due to [an hardcoded limitation](https://github.com/mozilla/kuma/blob/master/apps/wiki/feeds.py#L22) we cannot get further.

… We [raised the issue](https://github.com/webplatform/mdn-compat-importer/issues/3) and [Jérémie Patonnier pointed out something to help us](https://lists.w3.org/Archives/Team/team-devrel/2014Mar/0051.html).

… unfortunately it didn't help as [we are already doing this](https://github.com/webplatform/mdn-compat-importer/blob/master/lib/Reader.js#L197)

… currently we have good amount of data. It is incomplete, but good enough to make us have something working.

## Topic: Compat tables; how to work around limitation

… to work around the problem of hardcoded limitation from MDN. We have been suggested

… by one of our contributors, Pat Tressel, to use something specific for this. A software called \*Apache Nutch\* that is meant scraping websites to make a local copy

… w/ Nutch we'll be able to crawl the entire site and shouldn't hit too hard the MDN servers.

renoirb: we are talking about the crawler for the content to have it offline

… ptressel is doing this work with Nutch

<http://docs.webplatform.org/test/css/properties/max-height#Testing_CompaTables>

<http://docs.webplatform.org/test/css/properties/break-before#Testing_CompaTables>

ptressel

...or w/ a hand-written crawler in node.js if nutch isn't sufficiently configurable.

Renoirb: … in these pages, when mdn is matched, we extend the template.

… sometimes, we have to put the tag manually

… more efficient than reading json and generating page per visitor

… Next steps: do this with caniuse.com.

… compare and merge

julee: when will this be ready for the wiki pages?

renoirb: all css properties pages can be done right now.

renoirb

<http://docs.webplatform.org/compat/compat-mdn.json>

… barrier: hugh json object key

renoirb

search break-before

julee: what are the steps to adding the json

renoirb: clunky json. take svg, for example

… user has to search for json.

… I will make a prettified version

… but it would take a lot of time

… contributor would search for the key

… I'm in this media query, so here's how it's called

julee: can renoirb write the steps out?

renoirb: will write out the steps and show how you can get the key (in a more user-friendly way)

AI: renoirb will do this in a week or so

renoirb: eliezerb did some work on the flags

… we should get eliezerb on a conference call

julee: what do you need from eliezerb?

eliezerb

renoirb: I'm not able to join VoIP but we can do a quick hangout/skype conf later

renoirb: to know what he needs to finalize the flags.

renoirb

yes

eliezerb \^

eliezerb: we're done with this topic. Will you please email what you need to finalized the flags or get together with renoirb & shepazu to talk about any issues

next topic: content cleanup

renoirb: when I made the static site on github and we changed the home page

… nodejs static site generator. github clone to work on static site

eliezerb

julee: we already have a an open thread about this -\> <http://lists.w3.org/Archives/Public/public-webplatform/2014Apr/0036.html>

… stuff we don't need to generate dynamically

… I'm going to make a script to minify

… Jen suggested to change the menu as well

… we con't have "Issues" anymore

… where do we want it?

… I removed the "talk" menu item

… we still need "issues"

… but Jen doesn't want it on the global nav

renoirb

<http://www.webplatform.org/talk/>

<http://www.webplatform.org/talk/chatlogs/>

julee: but our primary persona is contributors who should file bugs

renoirb

Lets defer for the next meeting about that

AI: Julee to email Jen & the list

re: removal of issues from global nav

topic: single sign-on

renoirb: needs help with the resource server

jswisher: sent renoirb information of team members whom he can ask

renoirb

<http://notes.webplatform.org/>

topic: annotations system is live

renoirb wants to merge these accounts

… saw the code, saw why it wasn't working

… he'll be able to reuse what we already have

frozenice

renoirb: remember to get the WebSocket \_\_streamer\_\_ for annotations up

meeting over.
