Most articles automatically maintain a history of all edits and who made them. However, some articles are seeded with already-comprehensive content that comes from external sites. Maintaining a link to the original content helps give credit to those sites, maintain a historical link to the original copy in case it is necessary in the future, and in some cases it is required by the license of the original source.

==Adding external attribution to an article==

External attribution for a site should be added to an article when:

* You are copying in text from an existing WPD article that contains external attribution (including when you are merging articles)
* You are directly copying in a substantial piece of text (TODO: check what such a limit should be), from a site that is already listed in the external attribution list, below. When in doubt about if the text is substantial, assume it is. (Remember to always ensure the license of the origin site is compatible with copying the text to this site before copying, even for sites already on the external attribution list.)
* '''Mixing in content with a CC-BY-SA license adds a lot of administrative overhead (WPD uses a different license) and should be avoided if at all possible.''' If the text is short enough, consider rewriting it in your own words instead of copying directly. Any content that is licensed CC-BY-SA '''must''' be wrapped in a <code>&lt;div class='license-cc-by-sa'&gt;</code> to make it clear which portions of the content are under that license. See the Dealing With CC-BY-SA content section below for more information.

To add external attribution to an article, choose "Edit with Form" and check off the applicable box in the bottom of the form. Providing the actual link is optional in most cases; if it's not provided it will default to the organization's information page on WPD.

'''Special note for Mozilla Developer Network content''': Mozilla Developer Network content is licensed under a CC-BY-SA license. If the article you are editing contains content originally from that site and the license has ''not'' [[WPD:Porting_MDN_Content | been converted to the WPD license]], you '''must check off the CC-BY-SA checkbox''' when editing the article and '''include a link to the original site.''' Again, think carefully before mixing in CC-BY-SA content, as it is a different license from the rest of the site. See the Dealing With CC-BY-SA content section below for more information.

==Canonical list of sites that are on the external attribution list==

The canonical list of external attribution sites will be maintained at [[Template:External_Attribution]] in the future. It will contain:
* [http://developer.mozilla.com MDN]
* [http://www.html5rocks.com HTML5Rocks]
* [http://www.MSDN.com MSDN]
* ''and some others''

This list will populate the article-editing form.

==Maintaining the list of external attribution sites==

The list of sites that get external attribution is deliberately kept small. All items on the list should:
* Have at least five articles on WPD that would list that site for external attribution
* Be a well-regarded site that the community feels has valuable and accurate content.

If you believe that there is a site that fulfills these requirements that is not yet on the list, contact an administrator to have them add it to the canonical list.

==Dealing with CC-BY-SA content==
In some cases there will be portions of content that come from the Mozilla Developer Network that maintain their CC-BY-SA license (as opposed to the default CC-BY license for WPD). Maintaining content under multiple licenses is an administrative burden, and it is our long-term goal to remove CC-BY-SA licensed content from the site.

These portions of content must be clearly marked in the wikitext with <code>&lt;div class='license-cc-by-sa'&gt;</code>. Those divs may not be removed until the license has [[WPD:Porting_MDN_Content | been converted to the WPD license]]. Any edits inside that box should retain the box.

You can remove that box by rewriting the content inside the box in your own words and removing the original content inside that box.

An article should have the CC-BY-SA configuration box checked in the "Edit with Form" page if and only if there are some <code>&lt;div class='license-cc-by-sa'&gt;</code> blocks in the article.

==Example box==

For articles with some CC-BY-SA content:

<syntaxhighlight lang="html5">
&lt;details&gt;
	&lt;summary&gt;This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.&lt;/summary&gt;
	&lt;div&gt;
		Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
&lt;a href="http://developer.mozilla.org/foo" target="_blank"&gt;Foo&lt;/a&gt;
	&lt;/div&gt;
	&lt;div&gt;
		Portions of this content come from Foo.org: &lt;a href="http://foo.org/baz" target="_blank"&gt;Baz&lt;/a&gt;
	&lt;/div&gt;
&lt;/details&gt;
</syntaxhighlight>

For articles with no CC-BY-SA content:

<syntaxhighlight lang="html5">
&lt;details&gt;
	&lt;summary&gt;This article contains content originally from external sources.&lt;/summary&gt;
	&lt;div&gt;
		 Portions of this content come from the Mozilla Developer Network:
&lt;a href="http://developer.mozilla.org/foo" target="_blank"&gt;Foo&lt;/a&gt;
	&lt;/div&gt;
	&lt;div&gt;
		Portions of this content come from Foo.org: &lt;a href="http://foo.org/baz" target="_blank"&gt;Baz&lt;/a&gt;
	&lt;/div&gt;
&lt;/details&gt;
</syntaxhighlight>

TODO: some browsers don't support the details element, so we'll need a polyfill.