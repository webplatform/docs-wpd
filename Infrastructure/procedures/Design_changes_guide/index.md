= Design changes guide =

== Changes on the main style, or the wiki ==

In most cases, you want to edit screen.css, which is under /srv/salt/code/docs/current/skins/webplatform. This not only controls the wiki style, but also the main style for every section of the website, since it’s included in every section and then partially overriden by extra CSS files. There is also WebPlatform.php under /srv/salt/code/docs/current/skins, which controls the HTML generated.

After making your change, you need to commit & push it to [http://github.com/webplatform/mediawiki/ Github]. You can do that via 

  git commit -a -m 'Message explaining the changes' && git push
	
After the push is finished, you need to clone and deploy. We have a script that does it automatically. You will need to ssh into the server via:

  ssh 15.185.100.127
	
then get root privileges via 

  sudo su -
	
and then you just run

  deploy.sh skins
	
This deploys to docs_test, which you can find at http://docs.webplatform.org/test . If you want to deploy straight to docs_current, you can add the -c parameter, like so:

  deploy.sh -c skins
	
Otherwise, after you’ve checked your changes on the test wiki, you can deploy them to the current one through running:

  salt-run deploy.run code.docs_current
	
Of course you could still do by running deploy.sh again with the -c parameter, but this way you don’t pointlessly clone again from the Github repo.

After deploying, you might have to wait a bit until changes are reflected on the site, both for docs_test, and docs_current.

== Homepage or static files ==

The static files are under /srv/salt/code/nonshared/webplatform and do not currently have a git repository. The assets directory includes the CSS for the homepage (landing.css) and any image files, and the templates directory includes bits of HTML that are used accross multiple pages through PHP includes. To make a change there, you upload the changed files through FTP and then you run:

  salt-run deploy.run code.nonshared
	
on SSH, as root. As previously, you may need to wait a few minutes for your changes to be reflected. 

== Blog ==

The blog runs Wordpress and you can find the theme files under /srv/salt/code/blog/current/wp-content/themes/webplatform . As previously, to make a change you just upload the changed files and run:

  salt-run deploy.run code.blog
	
== The Bug Genie ==

The main bug genie CSS resides under /srv/salt/code/buggenie/thebuggenie/themes/webplatform/webplatform.css. 
The templates are scattered all around. You should read [http://docs.webplatform.org/wiki/WPD:Skinning_the_bug_genie Skinning Bug Genie] for more details on this. After you make a change, you upload it through FTP and run: 

  salt 'project*' state.sls code.buggenie
	
You don’t have to wait for the cache here, as there’s no cache involved.

== Tips & Gotchas ==

* When possible, you should strive to use colors already in our palette instead of inventing new ones, for consistency. You can find our color palette [http://docs.webplatform.org/wiki/WPD:Design#Colors here].
* Single-color icons are (or should be) found in our symbol font, WPSymbols, under /srv/salt/code/docs/current/skins/webplatform/fonts. It’s generated through http://icomoon.com/ . To edit it, you should upload WPSymbols.dev.svg (in the directory previously mentioned) to IcoMoon.