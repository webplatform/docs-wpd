{{Flags}}
{{Basic Page}}
==Overview==
This topic provides guidance for writing code and markup samples and snippets for documentation published to webplatform.org. It is meant to provide a quality bar for code samples and snippets, and to provide consistency of style across this documentation, not functionality. 
Sample code serves as a mini-portal to content. Developers use samples as documentation, and they almost always browse code before reading a topic fully. Because of its special regard, code requires special attention.
At the most basic level, effective code samples and snippets should follow these top five guidelines:
*It must run as intended. While you need not include an entire .html file, code samples should indicate where the code fits in with required elements. 
*Code samples and snippets should be simple and brief. Their purpose is to demonstrate specific functionality, not what a clever programmer you are. 
*Follow coding best practices, where they are clear. For example, use feature detection rather than browser sniffing. 
*Ensure that the text leading up to the sample code has a clear description of what that code accomplishes. List any assumptions the code sample or snippet makes and state prerequisites clearly and completely in its description. 
*List any requirements for each code sample or snippet in its description. 
==Types of sample code==
Broadly speaking, there are two sizes for example code: code snippets and code samples. 
'''Code snippet''': A code snippet is any example in the documentation. It shows how to use a specific member or how to accomplish a specific task. It might be a short snippet that focuses on a specific task (for example, how to cause a button to change color using the <code>onhover</code> event), or a longer tutorial or how-to. The code shown may not even compile out of context, but ideally it should be possible to paste the code into an existing project without extensive rewriting. A code snippet is real code; it is not pseudocode.
'''Code sample''': A code sample is intended to demonstrate programming tasks or scenarios, or to demonstrate a particular program architecture that is not easily demonstrated in a code snippet (for example, how to create, populate, and manage a list). A code sample is a complete, web page or application, with references to all required source files in its description.
When you approach a code sample, try to put yourself in the readers’ shoes. Ask yourself questions like these to enhance your samples and the content around them:
*“What do I want to learn from this sample?” (Not “What do I want to see this sample do.”)
*“What parts would I want to take from this sample, and how do I find them?”
*“How do I know that specific code blocks do what it looks like they are supposed to do?”
*“How can I map my own input and output requirements to those demonstrated in the sample code components?”
*“Can I cut-and-paste most of this into a webpage and make what I believe to be the minimal appropriate amount of changes, successfully?”
*“Where do I go to learn more? What OTHER resources are easily available?” 
==Best practices==
Creating code snippets or developing full samples share many best practices:
*Comment your code well. It can be frustrating to have to determine what a sample is doing at any one point.
*Keep it easy to scan the code. 
**Use consistent indenting and other formatting. WPD uses two spaces for each indentation. 
**Ensure the sample flows logically from start to finish.
*Keep the sample focused. If you find yourself using a lot of code branching, you’re probably trying to tackle too much.
*Use common patterns from the computer science lexicon. For example, use the MVC pattern rather than mingling the modules.
WPD uses some specific guidelines for HTML:
*Use lowercase letters for element names
*Place all attribute values in quotation marks
*Replace empty attributes with values, such as defer=”defer”
*Use a valid DOCTYPE, preferably <!DOCTYPE html>
*Avoid browser-sniffing. Test for feature presence instead.
*Avoid inline styles. They make the code harder to read.
WPD uses some specific guidelines for JavaScript
*Check for errors via exceptions. 
*Remember your semi-colons.
*Use the following pattern to create Singleton objects:
<pre>var Singleton = (function() {
var privateVariable = ”…”;
  this.publicMethod = function()	{…};
  function privateMethod() {…};
})();</pre>
*Use JavaScript namespaces to isolate variables and functionality from the global namespace for anything beyond simple illustrations.  This makes it simpler to copy-paste sample code into other pages.
*If every member in your namespace is public, use object-notation to create your namespace:
<pre>var SampleNamespace = {
  “init” : function() {…},
  “destroy” : function() {…},
  “defaultValue” : “…”,
    “NestedNamespace” : {
    “member” : “...”
    }
}</pre>
*If your namespace requires private members, use the singleton pattern. You can combine both patterns as you nest namespaces.
*All JSON structures should be well-formed and conform to the JSON specification [http://www.json.org http://www.json.org].
*Use <code>JSON.parse()</code> and <code>JSON.stringify()</code> to parse and serialize JSON strings.


The final suggestions: Be simple. Be straightforward. Don’t try to impress. Just teach.
{{Topics}}
{{External_Attribution
|Is_CC-BY-SA=No
|MDN_link=
|MSDN_link=
|HTML5Rocks_link=
}}