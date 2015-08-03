---
title: WPD:Manual Of Style/Code sample best practices
---
<h1><span class="mw-headline" id="Code_sample_best_practices">Code sample best practices</span></h1>
<h2><span class="mw-headline" id="Summary">Summary</span></h2>
<p>Guidelines to follow for developing code samples in Web Platform Docs.
</p>
<h2><span class="mw-headline" id="Overview">Overview</span></h2>
<p>This topic provides guidance for writing code and markup samples and snippets for documentation published to webplatform.org. It is meant to provide a quality bar for code samples and snippets, and to provide consistency of style across this documentation, not functionality. 
Sample code serves as a mini-portal to content. Developers use samples as documentation, and they almost always browse code before reading a topic fully. Because of its special regard, code requires special attention.
</p><p>At the most basic level, effective code samples and snippets should follow these top five guidelines:
</p>
<ul><li>It must run as intended. While you need not include an entire .html file, code samples should indicate where the code fits in with required elements. </li>
<li>Code samples and snippets should be simple and brief. Their purpose is to demonstrate specific functionality, not what a clever programmer you are. </li>
<li>Follow coding best practices, where they are clear. For example, use feature detection rather than browser sniffing. </li>
<li>Ensure that the text leading up to the sample code has a clear description of what that code accomplishes. List any assumptions the code sample or snippet makes and state prerequisites clearly and completely in its description. </li>
<li>List any requirements for each code sample or snippet in its description. </li></ul>
<h2><span class="mw-headline" id="Types_of_sample_code">Types of sample code</span></h2>
<p>Broadly speaking, there are two sizes for example code: code snippets and code samples. 
</p><p><b>Code snippet</b>: A code snippet is any example in the documentation. It shows how to use a specific member or how to accomplish a specific task. It might be a short snippet that focuses on a specific task (for example, how to cause a button to change color using the <code>onhover</code> event), or a longer tutorial or how-to. The code shown may not even compile out of context, but ideally it should be possible to paste the code into an existing project without extensive rewriting. A code snippet is real code; it is not pseudocode.
</p><p><b>Code sample</b>: A code sample is intended to demonstrate programming tasks or scenarios, or to demonstrate a particular program architecture that is not easily demonstrated in a code snippet (for example, how to create, populate, and manage a list). A code sample is a complete web page or application, with references to all required source files in its description.
</p><p>When you approach a code sample, try to put yourself in the readers’ shoes. Ask yourself questions like these to enhance your samples and the content around them:
</p>
<ul><li>“What do I want to learn from this sample?” (Not “What do I want to see this sample do?”)</li>
<li>“What parts would I want to take from this sample, and how do I find them?”</li>
<li>“How do I know that specific code blocks do what it looks like they are supposed to do?”</li>
<li>“How can I map my own input and output requirements to those demonstrated in the sample code components?”</li>
<li>“Can I cut-and-paste most of this into a webpage and successfully implement the code with minimal changes?”</li>
<li>“Where do I go to learn more? What OTHER resources are easily available?” </li></ul>
<h2><span class="mw-headline" id="Best_practices">Best practices</span></h2>
<p>Creating code snippets or developing full samples share many best practices:
</p>
<ul><li>Comment your code well. It can be frustrating to have to determine what a sample is doing at any one point. For example, see <a rel="nofollow" class="external free" href="http://code.webplatform.org/gist/9011914">http://code.webplatform.org/gist/9011914</a>.</li>
<li>Keep it easy to scan the code. 
<ul><li>Use consistent indenting and other formatting. WPD uses two spaces for each indentation. </li>
<li>Ensure the sample flows logically from start to finish.</li></ul></li>
<li>Keep the sample focused. If you find yourself using a lot of code branching, you are probably trying to tackle too much.</li>
<li>Use common patterns from the computer science lexicon. For example, use the MVC pattern rather than mingling the modules.</li></ul>
<p>WPD uses some specific guidelines for HTML:
</p>
<ul><li>Use lowercase letters for element names.</li>
<li>Place all attribute values in quotation marks.</li>
<li>Replace empty attributes with values, such as <code>defer="defer"</code></li>
<li>Use a valid DOCTYPE, preferably <code>&lt;!DOCTYPE html&gt;</code></li>
<li>Avoid browser-sniffing. Test for feature presence instead.</li>
<li>Avoid inline styles. They make the code harder to read.</li></ul>
<p>WPD uses some specific guidelines for JavaScript:
</p>
<ul><li>Check for errors via exceptions. </li>
<li>Remember your semi-colons.</li>
<li>Use the following pattern to create Singleton objects:</li></ul>
<pre>var Singleton = (function() {
var privateVariable = &quot;…&quot;;
  this.publicMethod = function()	{…};
  function privateMethod() {…};
})();</pre>
<ul><li>Use JavaScript namespaces to isolate variables and functionality from the global namespace for anything beyond simple illustrations. This makes it simpler to copy-paste sample code into other pages.</li>
<li>If every member in your namespace is public, use object-notation to create your namespace:</li></ul>
<pre>var SampleNamespace = {
  &quot;init&quot;&#160;: function() {…},
  &quot;destroy&quot;&#160;: function() {…},
  &quot;defaultValue&quot;&#160;: &quot;…&quot;,
    &quot;NestedNamespace&quot;&#160;: {
    &quot;member&quot;&#160;: &quot;...&quot;
    }
}</pre>
<ul><li>If your namespace requires private members, use the singleton pattern. You can combine both patterns as you nest namespaces.</li>
<li>All JSON structures should be well-formed and conform to the JSON specification <a rel="nofollow" class="external free" href="http://www.json.org">http://www.json.org</a>.</li>
<li>Use <code>JSON.parse()</code> and <code>JSON.stringify()</code> to parse and serialize JSON strings.</li></ul>
<h2><span class="mw-headline" id="Creating_a_live_code_example">Creating a live code example</span></h2>
<p>You can create a live code example on <a rel="nofollow" class="external text" href="http://code.webplatform.org/">code.webplatform.org</a> to add to your content. Live code can be a good addition to in-page snippets. To add code to code.webplatform.org and link to it, follow these steps. 
</p>
<ol><li> Once on code.webplatform.org, press <b>Ctrl + N</b> or <b>⌘ + N</b> to get a new example. Delete any boilerplate code.  </li>
<li> On each tab - CSS, HTML, and JS - break down your example by language section, and put the code on its respective tab. For the main JavaScript function, you don't need to include a function name. The magic behind code.webplatform.org executes your JavaScript once the HTML has loaded. Additional JavaScript functions that are called, however, do need to be defined with a function and name. </li>
<li> The <code>body</code> and <code>head</code> tags are not needed.</li>
<li> In the first line of code on the <code>CSS</code> tab, add a CSS comment with the title of your example, such as <code>/* Button example */</code>. You must add a comment do regardless of whether you have CSS content or not. This is essentially the same as using <code>title</code> in the head of a webpage. </li>
<li> Click the <code>Result</code> tab to see your example. The title for the page tab should be the same as the title of the CSS comment. </li>
<li> Click the <code>All</code> tab, and then press <b>CTRL + S</b> or <b>⌘ + S</b> to save the page. By saving from the <code>All</code> tab, users will automatically see your code executed when they land on the page. </li>
<li> Copy the URL from the address bar and paste it into the "Live example URL (optional)" field in your topic. </li></ol>
<p>A special note about using the Save button at the top of code.webplatform.com:
</p>
<ul><li> To see save options, hover your mouse over the Save button (it has an icon of an arrow pointing up into a cloud). The drop-down menu shows options for saving your code. If you click either the button or the arrow, the site automatically saves your sample. </li></ul>
<p>Some final suggestions: Be simple. Be straightforward. Do not try to impress. Just teach.
</p><p><br />
</p><p><br />
</p>
<div class="attribution">
<p><br />
</p><p><br />
</p>
</div>

<!-- 
NewPP limit report
CPU time usage: 0.055 seconds
Real time usage: 0.068 seconds
Preprocessor visited node count: 123/1000000
Preprocessor generated node count: 798/1000000
Post‐expand include size: 484/2097152 bytes
Template argument size: 218/2097152 bytes
Highest expansion depth: 5/40
Expensive parser function count: 0/100
-->

<!-- 
Transclusion expansion time report (%,ms,calls,template)
100.00%   48.076      1 - -total
 26.50%   12.740      1 - Template:Flags
 22.29%   10.715      1 - Template:Page_Title
 14.95%    7.189      1 - Template:External_Attribution
 11.57%    5.561      1 - Template:Summary_Section
  8.09%    3.891      1 - Template:Notes_Section
  6.11%    2.939      1 - Template:Topics
  4.91%    2.360      1 - Template:Basic_Page
-->

<!-- Saved in parser cache with key wpwiki:pcache:idhash:1079-0!*!*!!*!*!*!esi=1 and timestamp 20150731093029 and revision id 54687
 -->
