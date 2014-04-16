renoirb: compat tables

… we're crawling what we can on the site

… Jérémie Patonnier is aware of this

… we're still trying to get deeper, but there's a hardcoded limitation

… we're creating a crawler with apache sw to crawl & keep a copy of pages: Nutch

… w/ Nutch, we can get the content and we already have a new model

… in the test wiki we can see the compat tables from mdn

… we are using includes with memcache

… we can crawl, we can get a table, we can normalize what we get

… we modify, add notes or removing notes, for example, if it's mozilla-specific

… there's a limitation in the python pager

… we don't want to hammer the server, but crawl the pages once we get them

Apache Nutch

ptressel:

ohai  

renoirb: we are talking about the crawler for the content to have it offline

… ptressel is doing this work with Nutch

http://docs.webplatform.org/test/css/properties/max-height#Testing_CompaTables

http://docs.webplatform.org/test/css/properties/break-before#Testing_CompaTables

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

http://docs.webplatform.org/compat/compat-mdn.json

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

eliezerb ^

eliezerb: we're done with this topic. Will you please email what you need to finalized the flags or get together with renoirb & shepazu to talk about any issues

next topic: content cleanup

renoirb: when I made the static site on github and we changed the home page

… nodejs static site generator. github clone to work on static site

eliezerb

julee: we already have a an open thread about this -> http://lists.w3.org/Archives/Public/public-webplatform/2014Apr/0036.html

… stuff we don't need to generate dynamically

… I'm going to make a script to minify

… Jen suggested to change the menu as well

… we con't have "Issues" anymore

… where do we want it?

… I removed the "talk" menu item

… we still need "issues"

… but Jen doesn't want it on the global nav

renoirb

http://www.webplatform.org/talk/

http://www.webplatform.org/talk/chatlogs/

julee: but our primary persona is contributors who should file bugs

renoirb

Lets defer for the next meeting about that

AI: Julee to email Jen & the list

re: removal of issues from global nav

topic: single sign-on

renoirb: needs help with the resource server

jswisher: sent renoirb information of team members whom he can ask

renoirb

http://notes.webplatform.org/

topic: annotations system is live

renoirb wants to merge these accounts

… saw the code, saw why it wasn't working

… he'll be able to reuse what we already have

frozenice

renoirb: remember to get the WebSocket __streamer__ for annotations up  

meeting over.