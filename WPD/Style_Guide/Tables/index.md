---
title: Tables
uri: 'WPD:Style Guide/Tables'

---
## <span>Syntax</span>

For consistency and compatibility of tables, please use the following table syntax styles. These rules are required to ensure that tables print correctly in all contexts, including when they are part of a form field.

### <span>Normal pages</span>

    {|
    ! head 1
    ! head 2
    ! head 3
    |-
    | column a1
    | column a2
    | column a3
    |-
    | column b1
    | column b2
    | column b3
    |}

This results in the following table:

|head 1|head 2|head 3|
|:-----|:-----|:-----|
|column a1|column a2|column a3|
|column b1|column b2|column b3|

### <span>Form-based pages</span>

Tables in a template or form-based page must use the ["pipe hack"](/WPD:Manual_Of_Style/Gotchas#The_dreaded_pipe_character) instead of the `|` character:

    {{!}}

Thus, the same table in a form would use the following (ugly) syntax:

    {{{!}}
    ! head 1
    ! head 2
    ! head 3
    {{!}}-
    {{!}} column a1
    {{!}} column a2
    {{!}} column a3
    {{!}}-
    {{!}} column b1
    {{!}} column b2
    {{!}} column b3
    {{!}}}

### <span>Do not do this!</span>

Do not use the single-line row syntax.

    {|
    | head 1    !! column 2  !! column 3
    |-
    | column a1 || column a2 || column a3
    |-
    | column b1 || column b2 || column b3
    |}

## <span>Sortable tables</span>

MediaWiki has the ability to create [sortable tables](http://www.mediawiki.org/wiki/Help:Sorting), simply by adding the class `sortable`:

    {| class="sortable"
    ! head 1
    ! head 2
    ! head 3
    |-
    | apple a1
    | peach a2
    | blueberry a3
    |-
    | ape b1
    | dog b2
    | fish b3
    |}

This results in the following table:

|head 1|head 2|head 3|
|:-----|:-----|:-----|
|apple 1|peach 2|blueberry 3|
|ape 1|dog 2|zebra 3|

## <span>Other, less styled variant</span>

This variant has been found by mix-matching class names. Consider this as a hack if you really need to put data in a table without being forced to use first row as the table heading cell.

    {| class="mw-datatable os-suggest-results filehistory"
    |+Unstyled table, and showing table caption cell syntax
    |-
    |Column one
    |Column two
    |Column three
    |-
    |'''Column one and row one'''
    |Column two:
    * Lists
    * works
    * that way
    |Column three
    |-
    |'''Column one and row two'''
    |Column two, row two
    |Column three, row two
    |}

This results in the following table:

<table>
<caption>Unstyled table, and showing table caption cell syntax</caption>
<col width="33%" />
<col width="33%" />
<col width="33%" />
<tbody>
<tr class="odd">
<td align="left">Column one</td>
<td align="left">Column two</td>
<td align="left">Column three</td>
</tr>
<tr class="even">
<td align="left"><strong>Column one and row one</strong></td>
<td align="left">Column two:
<ul>
<li>Lists</li>
<li>works</li>
<li>that way</li>
</ul></td>
<td align="left">Column three</td>
</tr>
<tr class="odd">
<td align="left"><strong>Column one and row two</strong></td>
<td align="left">Column two, row two</td>
<td align="left">Column three, row two</td>
</tr>
</tbody>
</table>

