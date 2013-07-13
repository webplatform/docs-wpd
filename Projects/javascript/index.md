=JavaScript project proposal=
JavaScript is a proposed Web Platform Docs project to document the implementation of the ECMAScript standard in web browsers, focusing on the language itself rather than how it is coupled inside a browser to dom objects, events, HTML5 APIs, or CSS style.

==Project characteristics==
; Version: The version of JavaScript documented will be based on the ECMA-262 edition 5 standard of December 2009, since it has the [https://en.wikipedia.org/wiki/ECMAScript#Implementations largest browser support].  <span style="color:gray; font-size: smaller">Or possibly ECMA-262 edition 5.1 of June 2011.</span>

; Location: All JavaScript reference material will exist relative to the [[javascript|"javascript"]] parent page.

==Templates and forms==
Forms for all pages will be developed to allow editing with Semantic Forms rather than basic Mediawiki markup.

Two forms have been defined and are listed on the [[WPD:New_Page|new page tool]], JavaScript Operator and JavaScript Statement.  However, we are missing a form for JavaScript built-in objects.

Semantic query tests using the [[Special:Ask|semantic query interface]] should be made.  Investigation will be made whether or not JavaScript should be supported in queries.  This involves making the forms more semantic web aware, not only for the sake of page metadata like authorship and page date, but also so that assertions can be made about the parts of the language or built-in objects.  Reference about the extensions:
:: [http://www.mediawiki.org/wiki/Extension:Semantic_Forms Semantic Forms]
:: [http://www.mediawiki.org/wiki/Extension:Semantic_MediaWiki Semantic MediaWiki]

==On-going work==
Work has already begun importing MSDN JS pages:
* Search discussion in the mailing list [http://lists.w3.org/Archives/Public/public-webplatform/]
* Discussed in [[WPD:Community/Meetings/General|Webplatform meetings]]
* Project tasks and bugs reported in the  [http://project.webplatform.org/msdnjs MSDN conversion issue tracking]
* Guidelines [[WPD:Content/Reference_articles|Guidelines]]

Unfinished work or work not yet started:
* Create or update forms.
* Create a [[WPD:New_Page|new page tool]] for JavaScript
* Update the article [[WPD:Content/Reference_articles|reference page]] to fix the reference to the new page tool and update page location from old values like "js/operators"
* Format information during the MSDN JS import to conform to the form templates