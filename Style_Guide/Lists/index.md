---
title: WPD:Style Guide/Lists
---
<h2><span class="mw-headline" id="Syntax">Syntax</span></h2>
<p>For consistency and compatibility of lists, please use the following list syntax styles. These rules are required to ensure that tables print correctly in all contexts, including when they are part of a form field.
</p><p>Lists start each line with a token character, with additional tokens indicating the level of nesting of a list item.
</p>
<ul><li> The token for <a href="#Unordered_list">unordered lists</a> is the asterisk: <b>*</b></li>
<li> The token for <a href="#ordered_list">ordered lists</a> is the hash (or number sign): <b>#</b></li>
<li> The token for <a href="#definition_list">definition lists</a> <b>terms</b> is the semicolon: <b>;</b>
<ul><li> The token for definition list <b>definitions</b> is the colon: <b>:</b></li></ul></li></ul>
<p>There cannot be a space before the token, or it will not be converted to a list item. There cannot be a space between tokens.
</p><p>There cannot be a line break between list items, or it will start a new list.
</p><p>MediaWiki supports other list styles, but these are not allowed on Web Platform Docs, because of inadequate accessibility.
</p>
<h3><span class="mw-headline" id="Unordered_list">Unordered list</span></h3>
<p>Unordered lists (bulleted lists) start each line with an asterisk (*), with additional asterisks indicating the level of nesting of a list item (e.g., ** is a nested list item, *** is a double-nested list item).
</p>
<pre>
* This is a top-level item
* This is another top-level item
** This is a nested item
** This is another nested item
*** This is a nested item at the third level
* Line breaks&lt;br/&gt;don't break levels.
*** But jumping levels creates empty space.

* A blank line ends the list. This is the first bullet in a new list.
Any other start also ends the list.
* This is the first bullet in a new list.
 * This is not a list item, because there was a space before the token
</pre>
<p>This results in the following list:
</p>
<ul><li> This is a top-level item</li>
<li> This is another top-level item
<ul><li> This is a nested item</li>
<li> This is another nested item
<ul><li> This is a nested item at the third level</li></ul></li></ul></li>
<li> Line breaks<br />don't break levels.
<ul><li><ul><li> But jumping levels creates empty space.</li></ul></li></ul></li></ul>
<ul><li> A blank line ends the list. This is the first bullet in a new list.</li></ul>
<p>Any other start also ends the list.
</p>
<ul><li> This is the first bullet in a new list.</li></ul>
<pre>* This is not a list item, because there was a space before the token
</pre>
<h3><span class="mw-headline" id="Ordered_list">Ordered list</span></h3>
<p>Ordered lists (numbered lists) start each line with an asterisk (#), with additional asterisks indicating the level of nesting of a list item (e.g., ## is a nested list item, ### is a double-nested list item).
</p>
<pre>
# This is a top-level item
# This is another top-level item
## This is a nested item
## This is another nested item
### This is a nested item at the third level
# Line breaks&lt;br/&gt;don't break levels.
### But jumping levels creates empty space.

# A blank line ends the list. This is the first bullet in a new list.
Any other start also ends the list.
# This is the first bullet in a new list.
 # This is not a list item, because there was a space before the token
</pre>
<p>This results in the following list:
</p>
<ol><li> This is a top-level item</li>
<li> This is another top-level item
<ol><li> This is a nested item</li>
<li> This is another nested item
<ol><li> This is a nested item at the third level</li></ol></li></ol></li>
<li> Line breaks<br />don't break levels.
<ol><li><ol><li> But jumping levels creates empty space.</li></ol></li></ol></li></ol>
<ol><li> A blank line ends the list. This is the first bullet in a new list.</li></ol>
<p>Any other start also ends the list.
</p>
<ol><li> This is the first bullet in a new list.</li></ol>
<pre># This is not a list item, because there was a space before the token
</pre>
<h3><span class="mw-headline" id="Definition_list">Definition list</span></h3>
<p>Definition lists use slightly different sytnax:
</p>
<ul><li> The token for indicating the term to be defined is the semicolon: <b>;</b></li>
<li> The token for indicating the definition for that is the colon: <b>:</b></li></ul>
<p>Each term may have multiple definitions.
</p>
<pre>
; term 1
: definition for term 1
; term 2
: definition 1 for term 2
: definition 2 for term 2
</pre>
<p>This results in the following list:
</p>
<dl><dt> term 1</dt>
<dd> definition for term 1</dd>
<dt> term 2</dt>
<dd> definition 1 for term 2</dd>
<dd> definition 2 for term 2</dd></dl>
<h3><span class="mw-headline" id="Mixed_list">Mixed list</span></h3>
<p>Mixing tokens results in a mixed list
</p>
<pre>
# This is an ordered top-level item
#* This is a nested unordered item
#* This is another nested unordered item
# This is another ordered top-level item
#; This is a nested definition term item
#: This is a nested definition item
</pre>
<p>This results in the following list:
</p>
<ol><li> This is an ordered top-level item
<ul><li> This is a nested unordered item</li>
<li> This is another nested unordered item</li></ul></li>
<li> This is another ordered top-level item
<dl><dt> This is a nested definition term item</dt>
<dd> This is a nested definition item</dd></dl></li></ol>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:6541-0!*!*!!*!*!*!esi=1 and timestamp 20150731183117 and revision id 17683
 -->
