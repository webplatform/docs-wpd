---
title: Sprint of 2014-03
uri: 'WPD:Projects/CompaTables/201403-sprint'

---
Sprint report, extending documentation at [WPD:Projects/CompaTables](/WPD:Projects/CompaTables)

## Work done

**mdn-compat-importer**:

-   Process and normalize data (living implementation)

**CompaTables MediaWiki Extension**:

-   Implement mdn-compat-importer *[\#Current normalized data](#Current_normalized_data)* (living implementation)
-   Relies on Memcached to save/purge/re-use chunks of HTML
-   Allow manage markup-free text arrays (e.g. in format=table, the word "Unsupported" be in a dd tag, while in format=list it can be in a abbr tag)
-   Support alternate URL for table itself on its own view:
    -   [Table in a standard view](http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table)
    -   [Table alone (used for ESI, see in URL '&foresi=1')](http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table&foresi=1)
-   Purging Memcached version of generated HTML views:
    -   When origin JSON file date changes mismatch cached version
    -   Purging a particular table directly, along with ESI purging mechanism [see in URL note '&action=purge'](http://docs.webplatform.org/test/Special:Compatables?feature=border-radius&format=table&action=purge)
-   Should not break current ESI support feature
-   Rudimentary A11y markup (needs testing). Done according to [this WCAG1 checkpoint](http://www.w3.org/TR/WCAG10-HTML-TECHS/#identifying-table-rows-columns)

## To fix or improve

#### CompaTables MediaWiki Extension

-   List view format (format=list) is not using latest *[\#Current normalized data](#Current_normalized_data)*
-   Table view format
    -   doesn't show prefix icons (e.g. -webkit)

#### ESI

To use ESI, work has to be done on the servers. To summarize the findings, we cannot enable ESI tags on Fastly as it is at the moment due to a set of factors:

Fastly's Varnish version (2.1.5) doesn't support gzip between backend and varnish; (but Varnish 3.x+ do.)

-   Between our servers ("backend") and Fastly we use currently compress with gzip
-   Fastly has plans to upgrade their varnish, but its out of our hands

To enable;

-   Disable gzip between our backend servers and Fastly (might increase the data transfer usage, to validate with fastly)
-   Enable gzip only from Fastly to our visitors (currently gzip is in both places)
