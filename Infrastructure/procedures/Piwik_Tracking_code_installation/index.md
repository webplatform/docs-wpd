---
title: 'Piwik Tracking code installation'
uri: 'WPD:Infrastructure/procedures/Piwik Tracking code installation'

---
## Summary

How is installed the tracking code throughout the web application.

## Web applications

### BugGenie

-   File **core/templates/footer.inc.php** has the Piwik tracking code
-   Visitor exclusion: None

### MediaWiki

-   Based on [MediaWiki Piwik Integration](http://www.mediawiki.org/wiki/Extension:Piwik_Integration)
-   Created two files in *code/docs/current/extensions/piwik/*
-   Added file: [piwik-mediawiki-extension Piwik.hooks.php](https://raw.github.com/DaSchTour/piwik-mediawiki-extension/master/Piwik.php)
-   Added file from: [piwik-mediawiki-extension Piwik.php](https://raw.github.com/DaSchTour/piwik-mediawiki-extension/master/Piwik.php)
-   Modified code/docs/Settings.php accordingly to [6]
-   Visitor exclusion: None

### Status (tumblr)

-   Login to Tumblr, in Settings, WebPlatform.org site, Search for Theme, click 'customize', find 'Edit HTML' button, added code.
-   Visitor exclusion: None

### WordPress

-   Installed [Wp-Piwik plugin](http://wordpress.org/plugins/wp-piwik/)
-   Visitor exclusion: None

### Static pages

-   Edited in file: code/nonshared/webplatform/templates/container\_close.html
-   Used on the pages:
    1.  <http://talk.webplatform.org/>
    2.  <http://www.webplatform.org/errors/503.html>
    3.  <http://www.webplatform.org/errors/404.html>
    4.  <http://www.webplatform.org/stewards/adobe/> (and all other stewards)
    5.  <http://www.webplatform.org/logo/>
-   Visitor exclusion: None

### Customizations

#### MediaWiki

``` html
// In file Piwik.hooks.php, within AddPiwik method

    $wgPiwikCustomJS[] = <<<'JS'

          // Note from renoirb: Should be moved somewhere else soon
          jQuery(document).ready(function(){
              jQuery('body').on('click', '#ca-edit', function(){
                 if (typeof _paq !== 'undefined') {
                    _paq.push(['trackGoal',1]);// Goal specific to edit a page
                 }
              });
          });

JS;

    // Do NOT fail the attempt if it failed, please.
    try {
      if ( $wgUser->isAnon() === false ) {
        $userName = $wgUser->getName();
        $wgPiwikCustomJS[] = '          _paq.push(["setCustomVariable",1,"username","'.$userName.'", "visit"]);'.PHP_EOL;
      }
    } catch(Exception $e) {  }
```
