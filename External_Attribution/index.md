Most articles automatically maintain a history of all edits and who made them. However, some articles are seeded with already-comprehensive content that comes from external sites. Maintaining a link to the original content helps give credit to those sites, maintain a historical link to the original copy in case it is necessary in the future, and in some cases it is required by the license of the original source.

==Legal Note==
Note that there are some potential exceptions to our general policy on attribution and external sources:
* Documents that only state facts, and not interpretation, are not protected by copyright, and are thus outside the bounds of licensing . But this line can be gray... a compilation of facts is protected by copyright if the selection and arrangement of the material is original. Thus, if the contribution is based on another source, it's safer to provide and preserve attribution;
* If all the original material from a particular source has been excised from the article, attribution for that source can optionally be removed; in practice, however, we are only using this to deliberately simplify the license the article is available under, e.g., if the original content was under CC-BY-SA (Attribution and Share Alike), we might remove all the old material so the replacement article can be reused under CC-BY. Even so, we may choose to keep the original attribution for social reasons.

==Adding external attribution to an article==
External attribution for a site should be added to an article when:

* You are copying in text from an existing WPD article that contains external attribution (including when you are merging articles)
* You are directly copying in a substantial piece of text, from a site that is already listed in the external attribution list, below. When in doubt about if the text is substantial, assume it is. (Remember to always ensure the license of the origin site is compatible with copying the text to this site before copying, even for sites already on the external attribution list.) '''The guideline for substantial is: if it's long enough that it's possible to re-write the content in your own words'''. In practice, this means that simple facts (like which version a given feature was supported by a browser) aren't substantial, but things that are a sentence or more are. If you are bringing in content from one of these sources but is not substantial, you should still include attribution to the original source (just not apply the alternate license for that content).
* '''Mixing in content with a CC-BY-SA license adds a lot of administrative overhead (WPD uses a different license) and therefore such imports should be avoided if at all possible.''' This includes mixing in content from Mozilla Developer Network. If the text is short enough, consider rewriting it in your own words instead of copying directly. Any content that is licensed CC-BY-SA '''must''' be wrapped in a <code>&lt;div class='license-cc-by-sa'&gt;</code> to make it clear which portions of the content are under that license. See the [[#Dealing_With_CC-BY-SA_Content| Dealing With CC-BY-SA Content]] section below for more information.

To add external attribution to an article, choose "Edit with Form" and check off the applicable box in the bottom of the form. Providing the actual link is optional in most cases; if it's not provided it will default to the organization's information page on WPD.

'''Special note for Mozilla Developer Network content''': Mozilla Developer Network content is licensed under a CC-BY-SA license. If the article you are editing contains content originally from that site and the license has ''not'' [[WPD:Copyright | been converted to the WPD license]], you '''must check off the CC-BY-SA checkbox''' when editing the article and '''include a link to the original site.''' Again, think carefully before mixing in CC-BY-SA content, as it is a different license from the rest of the site. See the [[#Dealing_With_CC-BY-SA_Content| Dealing With CC-BY-SA Content]] section below for more information.

==Canonical list of sites that are on the external attribution list==

The canonical list of external attribution sites is maintained at [[Property:External_Attribution_Source]]. The list has been copied here for convenience: 
* [http://developer.mozilla.org MDN]
* [http://www.html5rocks.com HTML5Rocks]
* [http://www.MSDN.com MSDN]
* [http://developers.facebook.com/html5 Facebook HTML5 Resource Center]
* ''and some others''

This list will populate the article-editing form.

==Maintaining the list of external attribution sites==

The list of sites that get external attribution is deliberately kept small. All items on the list should:
* Have at least five articles on WPD that would list that site for external attribution
* Be a well-regarded site that the community feels has valuable and accurate content.

If you believe that there is a site that fulfills these requirements that is not yet on the list, contact an administrator to have them add it to the canonical list.

==Dealing with CC-BY-SA content==
In some cases there will be portions of content that come from sites with a CC-BY-SA license, like the Mozilla Developer Network (as opposed to the default CC-BY license for WPD). Maintaining content under multiple licenses is an administrative burden, and it is our long-term goal to remove CC-BY-SA licensed content from the site. Only sites in the canonical list of external attribution sites may have CC-BY-SA content ported over.

These portions of content must be clearly marked in the wikitext with <code>&lt;div class='license-cc-by-sa'&gt;</code>. Those divs may not be removed until the license has [[WPD:Copyright | been converted to the WPD license]]. Any edits inside that box should retain the box.

You can remove that box by rewriting the content inside the box in your own words and removing the original content inside that box.

An article should have the CC-BY-SA configuration box checked in the "Edit with Form" page if and only if there are some <code>&lt;div class='license-cc-by-sa'&gt;</code> blocks in the article.

Code without the CC-BY-SA configuration box checked falls under the normal license of the WPD, CC-BY.

==Example box==

For articles with some CC-BY-SA content:

<syntaxhighlight lang="html5">
<details>
  <summary>This article contains content originally from external sources, including ones licensed under the CC-BY-SA license.</summary>
  <p>
    Portions of this content copyright 2012 Mozilla Contributors. This article contains work licensed under the Creative Commons Attribution-Sharealike License v2.5 or later. The original work is available at Mozilla Developer Network:
<a href="http://developer.mozilla.org/foo" target="_blank">Foo</a>
  </p>
  <p>
    Portions of this content come from Foo.org: <a href="http://foo.org/baz" target="_blank">Baz</a>
  </p>
</details>
</syntaxhighlight>

For articles with no CC-BY-SA content:

<syntaxhighlight lang="html5">
<details>
  <summary>This article contains content originally from external sources.</summary>
  <p>
    Portions of this content come from the Mozilla Developer Network:
<a href="http://developer.mozilla.org/foo" target="_blank">Foo</a>
  </p>
  <p>
    Portions of this content come from Foo.org: <a href="http://foo.org/baz" target="_blank">Baz</a>
  </p>
</details>
</syntaxhighlight>

{{TODO | some browsers don't support the details element, so we'll need a polyfill.}}