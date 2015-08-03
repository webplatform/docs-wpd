---
title: WPD:Community/Meetings/General/2014/0415 raw mtg notes
---
<h2><span class="mw-headline" id="Topic:_Compat_tables">Topic: Compat tables</span></h2>
<p>renoirb: We have something working that use compatibility data from MDN
</p><p>… we cannot get all the data, more on this later, but we have enough to allow the community to use it already
</p><p>… you can see how it works from the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/">test wiki</a> and you can see many examples in the <a rel="nofollow" class="external text" href="http://docs.webplatform.org/test/Tests/Compatibility_table_and_caching">/test/Tests/Compatibility_table_and_caching page</a>.
</p><p>… Adding a table requires to use <code>&lt;compatability feature="analyser-node" format="table"&gt;&lt;/compatability&gt;</code> tag.
</p><p>… figuring out which key to put in <code>feature=""</code> can be found from a human-friendly JSON file at <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/compat-mdn-human.json">compat/compat-mdn-human.json</a>, it is a reformatted version from the raw <a rel="nofollow" class="external text" href="http://docs.webplatform.org/compat/compat-mdn.json">compat/compat-mdn.json file</a>
</p><p>… The project had many iterations:
</p><p>…  1. First iteration (led by Shepazu) was about generating HTML table based on JSON data file. The table was regenerated at every page render. If a visitor is logged in Mediawiki, it would regenerate at every page view (!)
</p><p>…  2. Second iteration (led by Aaron, a reference of Ryan Lane) was about leveraging Varnish's ESI tags that allows us to freeze snippets of HTML in a page. It went well, but it isn't deployed due to limitations with our Varnish provider (Fastly). It is using a version of Varnish that cannot GZIP content AND do ESI includes. At that point, we decided to focus on importing data
</p><p>…  3. Third iteration (led by Frozenice) was to create a nodejs crawler to copy and normalize the data.
</p><p>…  4. Most recent iteration (led by renoirb) was to work on normalizing
</p><p>…      the data and add continue improving the code. It now uses internally memcached to keep the generated HTML and will serve that version until the cache is invalidated.
</p><p>…     The cache can be invalidated if the original JSON file is updated, or if it has been purged or if the lifetime of the cached version comes.
</p><p>…     That way, regardless of whether Varnish provides us the ESI version, it adds one more performance improvement before hitting our servers
</p><p>… So, at the moment, we: have MDN data, can normalize it, do generate HTML tables, do have two layers of caching, have ways for users to embed the data in our wiki (!).
</p><p><br />
</p>
<h2><span class="mw-headline" id="Topic:_Compat_tables.3B_known_limitation">Topic: Compat tables; known limitation</span></h2>
<p>renoirb: As I said, we have a known limitation. 
… Our current implementation was already making a copy, but with a specific tool, we can concentrate <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer">mdn-compat-importer</a> only for normalizing the data 
</p><p>… what we are basically doing is crawling the pages, keeping a local copy as HTML to JavaScript object in files
</p><p>… the normalization is basically a second-pass, , is about
</p><p>… normalize what we think makes sense following Can I use's result
</p><p>… We move what we are unsure in notes or removing notes, for example, if it's mozilla-specific
</p><p><br />
renoirb: we have something working that creates a local copy of pages that has compatibility data
</p><p>… the scraping is not complete due to a known issue but it is a good starting point
</p><p>… eventually we will need to be aple to scrape everythin. But due to <a rel="nofollow" class="external text" href="https://github.com/mozilla/kuma/blob/master/apps/wiki/feeds.py#L22">an hardcoded limitation</a> we cannot get further.
</p><p>… We <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer/issues/3">raised the issue</a> and <a rel="nofollow" class="external text" href="https://lists.w3.org/Archives/Team/team-devrel/2014Mar/0051.html">Jérémie Patonnier pointed out something to help us</a>.
</p><p>… unfortunately it didn't help as <a rel="nofollow" class="external text" href="https://github.com/webplatform/mdn-compat-importer/blob/master/lib/Reader.js#L197">we are already doing this</a>
</p><p>… currently we have good amount of data. It is incomplete, but good enough to make us have something working.
</p><p><br />
</p>
<h2><span class="mw-headline" id="Topic:_Compat_tables.3B_how_to_work_around_limitation">Topic: Compat tables; how to work around limitation</span></h2>
<p>… to work around the problem of hardcoded limitation from MDN. We have been suggested 
</p><p>… by one of our contributors, Pat Tressel, to use something specific for this.  A software called *Apache Nutch* that is meant scraping websites to make a local copy
</p><p>… w/ Nutch we'll be able to crawl the entire site and shouldn't hit too hard the MDN servers.
</p><p>renoirb: we are talking about the crawler for the content to have it offline
</p><p>… ptressel is doing this work with Nutch
</p><p><a rel="nofollow" class="external free" href="http://docs.webplatform.org/test/css/properties/max-height#Testing_CompaTables">http://docs.webplatform.org/test/css/properties/max-height#Testing_CompaTables</a>
</p><p><a rel="nofollow" class="external free" href="http://docs.webplatform.org/test/css/properties/break-before#Testing_CompaTables">http://docs.webplatform.org/test/css/properties/break-before#Testing_CompaTables</a>
</p><p>ptressel
</p><p>...or w/ a hand-written crawler in node.js if nutch isn't sufficiently configurable.
</p><p>Renoirb: … in these pages, when mdn is matched, we extend the template.
</p><p>… sometimes, we have to put the tag manually
</p><p>… more efficient than reading json and generating page per visitor
</p><p>… Next steps: do this with caniuse.com.
</p><p>… compare and merge
</p><p>julee: when will this be ready for the wiki pages?
</p><p>renoirb: all css properties pages can be done right now.
</p><p>renoirb
</p><p><a rel="nofollow" class="external free" href="http://docs.webplatform.org/compat/compat-mdn.json">http://docs.webplatform.org/compat/compat-mdn.json</a>
</p><p>… barrier: hugh json object key
</p><p>renoirb
</p><p>search break-before
</p><p>julee: what are the steps to adding the json
</p><p>renoirb: clunky json. take svg, for example
</p><p>… user has to search for json.
</p><p>… I will make a prettified version
</p><p>… but it would take a lot of time
</p><p>… contributor would search for the key
</p><p>… I'm in this media query, so here's how it's called
</p><p>julee: can renoirb write the steps out?
</p><p>renoirb: will write out the steps and show how you can get the key (in a more user-friendly way)
</p><p>AI: renoirb will do this in a week or so
</p><p>renoirb: eliezerb did some work on the flags
</p><p>… we should get eliezerb on a conference call
</p><p>julee: what do you need from eliezerb?
</p><p>eliezerb
</p><p>renoirb: I'm not able to join VoIP but we can do a quick hangout/skype conf later
</p><p>renoirb: to know what he needs to finalize the flags.
</p><p>renoirb
</p><p>yes
</p><p>eliezerb ^
</p><p>eliezerb: we're done with this topic. Will you please email what you need to finalized the flags or get together with renoirb &amp; shepazu to talk about any issues
</p><p>next topic: content cleanup
</p><p>renoirb: when I made the static site on github and we changed the home page
</p><p>… nodejs static site generator. github clone to work on static site
</p><p>eliezerb
</p><p>julee: we already have a an open thread about this -&gt; <a rel="nofollow" class="external free" href="http://lists.w3.org/Archives/Public/public-webplatform/2014Apr/0036.html">http://lists.w3.org/Archives/Public/public-webplatform/2014Apr/0036.html</a>
</p><p>… stuff we don't need to generate dynamically
</p><p>… I'm going to make a script to minify
</p><p>… Jen suggested to change the menu as well
</p><p>… we con't have "Issues" anymore
</p><p>… where do we want it?
</p><p>… I removed the "talk" menu item
</p><p>… we still need "issues"
</p><p>… but Jen doesn't want it on the global nav
</p><p>renoirb
</p><p><a rel="nofollow" class="external free" href="http://www.webplatform.org/talk/">http://www.webplatform.org/talk/</a>
</p><p><a rel="nofollow" class="external free" href="http://www.webplatform.org/talk/chatlogs/">http://www.webplatform.org/talk/chatlogs/</a>
</p><p>julee: but our primary persona is contributors who should file bugs
</p><p>renoirb
</p><p>Lets defer for the next meeting about that
</p><p>AI: Julee to email Jen &amp; the list
</p><p>re: removal of issues from global nav
</p><p>topic: single sign-on
</p><p>renoirb: needs help with the resource server
</p><p>jswisher: sent renoirb information of team members whom he can ask
</p><p>renoirb
</p><p><a rel="nofollow" class="external free" href="http://notes.webplatform.org/">http://notes.webplatform.org/</a>
</p><p>topic: annotations system is live
</p><p>renoirb wants to merge these accounts
</p><p>… saw the code, saw why it wasn't working
</p><p>… he'll be able to reuse what we already have
</p><p>frozenice
</p><p>renoirb: remember to get the WebSocket __streamer__ for annotations up  
</p><p>meeting over.
</p>
<!-- Saved in parser cache with key wpwiki:pcache:idhash:19655-0!*!*!!*!*!*!esi=1 and timestamp 20150731185131 and revision id 51508
 -->
