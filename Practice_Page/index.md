{{Page_Title|:active}}
{{Flags
|Editorial notes=Practice page
|Checked_Out=Yes
}}
{{Standardization_Status|W3C Editor's Draft}}
{{API_Name}}
{{Summary_Section|The :active selector is used to select and style the active link.
A link becomes active when it is clicked and the characteristics that are applied remain for as long as the click is held.
}}
{{CSS Property
|Values=
}}
{{Examples_Section
|Not_required=No
|Examples={{Single Example
|Language=HTML
|Code=<!DOCTYPE html>
<html>
<head>
<style>
a:active {
    background-color: purple;
}
</style>
</head>
<body>

<a href="https://docs.webplatform.org/wiki/css/functions/blur</a>


<p><b>Note:</b> The :active selector styles the active link with the color purple.</p>

</body>
</html>
}}{{Single Example
|Language=HTML
|Description=The :active selector can be used on all elements, not only links. Below the lines become 'active' just by hovering.
|Code=<!DOCTYPE html>
<html>
<head>
<style>
a.ex1:hover, a.ex1:active {color: yellow;}
a.ex2:hover, a.ex2:active {font-size: 250%;}
a.ex3:hover, a.ex3:active {background: blue;}
a.ex4:hover, a.ex4:active {font-family: monospace;}
a.ex5:visited, a.ex5:link {text-decoration: none;}
a.ex5:hover, a.ex5:active {text-decoration: underline;}
</style>
</head>
<body>

<p>Mouse over the links to see them change layout.</p>

<p><a class="ex1" href="default.asp">This link changes color</a></p>
<p><a class="ex2" href="default.asp">This link changes font-size</a></p>
<p><a class="ex3" href="default.asp">This link changes background-color</a></p>
<p><a class="ex4" href="default.asp">This link changes font-family</a></p>
<p><a class="ex5" href="default.asp">This link changes text-decoration</a></p>

</body>
</html>
|LiveURL=https://code.webplatform.org/gist/c8bb944dbeddf68de2ec
}}
}}
{{Notes_Section
|Notes=Note: :active MUST come after :hover (if present) in the CSS definition in order to be effective!

Related selectors for links include the :link selector to style links to unvisited pages, the :visited selector to style links to visited pages, and the :hover selector to style links when you mouse over them.
}}
{{Related_Specifications_Section
|Specifications=
}}
{{See_Also_Section
|Topic_clusters=HTML
}}
{{Topics|HTML}}
{{External_Attribution
|Is_CC-BY-SA=No
}}
{{Compatibility_Section
|Not_required=Yes
|Imported_tables=
|Desktop_rows=
|Mobile_rows=
|Notes_rows=
}}