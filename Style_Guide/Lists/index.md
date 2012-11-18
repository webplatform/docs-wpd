==Syntax==
For consistency and compatibility of lists, please use the following list syntax styles. These rules are required to ensure that tables print correctly in all contexts, including when they are part of a form field.

Lists start each line with a token character, with additional tokens indicating the level of nesting of a list item.
* The token for [[#Unordered_list|unordered lists]] is the asterisk: '''*'''
* The token for [[#ordered_list|ordered lists]] is the hash (or number sign): '''#'''
* The token for [[#definition_list|definition lists]] '''terms''' is the semicolon: ''';'''
** The token for definition list '''definitions''' is the colon: ''':'''

There cannot be a space before the token, or it will not be converted to a list item. There cannot be a space between tokens.

There cannot be a line break between list items, or it will start a new list.

===Unordered list===
Unordered lists (bulleted lists) start each line with an asterisk (*), with additional asterisks indicating the level of nesting of a list item (e.g., ** is a nested list item, *** is a double-nested list item).

<pre><nowiki>
* This is a top-level item
* This is another top-level item
** This is a nested item
** This is another nested item
*** This is a nested item at the third level
* Line breaks<br/>don't break levels.
*** But jumping levels creates empty space.

* A blank line ends the list. This is the first bullet in a new list.
Any other start also ends the list.
* This is the first bullet in a new list.
 * This is not a list item, because there was a space before the token
</nowiki></pre>

This results in the following list:
* This is a top-level item
* This is another top-level item
** This is a nested item
** This is another nested item
*** This is a nested item at the third level
* Line breaks<br/>don't break levels.
*** But jumping levels creates empty space.

* A blank line ends the list. This is the first bullet in a new list.
Any other start also ends the list.
* This is the first bullet in a new list.
 * This is not a list item, because there was a space before the token

===Ordered list===
Ordered lists (numbered lists) start each line with an asterisk (#), with additional asterisks indicating the level of nesting of a list item (e.g., ## is a nested list item, ### is a double-nested list item).

<pre><nowiki>
# This is a top-level item
# This is another top-level item
## This is a nested item
## This is another nested item
### This is a nested item at the third level
# Line breaks<br/>don't break levels.
### But jumping levels creates empty space.

# A blank line ends the list. This is the first bullet in a new list.
Any other start also ends the list.
# This is the first bullet in a new list.
 # This is not a list item, because there was a space before the token
</nowiki></pre>

This results in the following list:
# This is a top-level item
# This is another top-level item
## This is a nested item
## This is another nested item
### This is a nested item at the third level
# Line breaks<br/>don't break levels.
### But jumping levels creates empty space.

# A blank line ends the list. This is the first bullet in a new list.
Any other start also ends the list.
# This is the first bullet in a new list.
 # This is not a list item, because there was a space before the token

===Definition list===
Definition lists use slightly different sytnax:
* The token for indicating the term to be defined is the semicolon: ''';'''
* The token for indicating the definition for that is the colon: ''':'''

Each term may have multiple definitions.

<pre><nowiki>
; term 1
: definition for term 1
; term 2
: definition 1 for term 2
: definition 2 for term 2
</nowiki></pre>

This results in the following list:
; term 1
: definition for term 1
; term 2
: definition 1 for term 2
: definition 2 for term 2

===Mixed list===
Mixing tokens results in a mixed list

<pre><nowiki>
# This is an ordered top-level item
#* This is a nested unordered item
#* This is another nested unordered item
# This is another ordered top-level item
#; This is a nested definition term item
#: This is a nested definition item
</nowiki></pre>

This results in the following list:
# This is an ordered top-level item
#* This is a nested unordered item
#* This is another nested unordered item
# This is another ordered top-level item
#; This is a nested definition term item
#: This is a nested definition item