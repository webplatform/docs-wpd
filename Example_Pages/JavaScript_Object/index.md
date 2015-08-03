---
title: WPD:Example Pages/JavaScript Object
---
<h1><span class="mw-headline" id="Summary">Summary</span></h1>
<p>JavaScript <code>Date</code> objects let you work with dates and times. 
</p><p>Enables basic storage and retrieval of dates and times.
</p>
<h1><span class="mw-headline" id="Overview_table">Overview table</span></h1>
<table class="wikitable">

<tr>
<td> Inherits from </td>
<td> <a href="/w/index.php?title=JS/Function&amp;action=edit&amp;redlink=1" class="new" title="JS/Function (page does not exist)">Function</a> (can be multiple links here)
</td></tr>
<tr>
<td> Descendents </td>
<td> any children
</td></tr></table>
<h1><span class="mw-headline" id="Constructor_syntax">Constructor syntax</span></h1>
<pre>new Date()
new Date(dateVal)
new Date(year, month, day [, hour, minute, second, millisecond])
</pre>
<p><i><b>Implementation Note:</b> link from the syntax block to the individual parameters; if possible, autogenerate the constructor syntax.</i>
</p>
<h2><span class="mw-headline" id="Parameters">Parameters</span></h2>
<dl><dt>dateVal</dt>
<dd> If an integer value, it represents the number of milliseconds since 1 January 1970 00:00:00 UTC (Unix Epoch). If a string, dateVal is parsed according to the rules in Formatting Date and Time Strings (JavaScript). In Microsoft Internet Explorer, the <i>dateVal</i> argument can also be a VT_DATE value as returned from some ActiveX objects.</dd>
<dt>year</dt>
<dd> Required. Integer value representing the year. For compatibility (in order to avoid the Y2K problem), you should always specify the year in full; use 1998, rather than 98.</dd>
<dt>month</dt>
<dd> Required. Integer value representing the month, beginning with 0 for January to 11 for December.</dd>
<dt>day</dt>
<dd> Required. Integer value representing the day of the month (1-31).</dd>
<dt>hour</dt>
<dd> Optional. Integer value representing the hour of the day (0-23).</dd>
<dt>minute</dt>
<dd> Optional. Integer value representing the minute segment (0-59) of a time reading.</dd>
<dt>second</dt>
<dd> Optional. Integer value representing the seconds segment (0-59) of a time reading.</dd>
<dt>millisecond</dt>
<dd> Optional. Integer value representing the millisecond segment (0-999) of a time reading.</dd></dl>
<h1><span class="mw-headline" id="Usage">Usage</span></h1>
<h2><span class="mw-headline" id="Constructor">Constructor</span></h2>
<p>Note: Note that JavaScript Date objects can only be instantiated by calling JavaScript Date as a constructor: calling it as a regular function (i.e. without the new operator) will return a string rather than a Date object; unlike other JavaScript object types, JavaScript Date objects have no literal syntax.
</p><p>If you supply no arguments, the constructor creates a JavaScript Date object for today's date and time according to local time. If you supply some arguments but not others, the missing arguments are set to 0. If you supply any arguments, you must supply at least the year, month, and day. You can omit the hours, minutes, seconds, and milliseconds.
</p><p>Invoking JavaScript Date in a non-constructor context (i.e., without the new operator) will return a string representing the current time.
</p>
<h2><span class="mw-headline" id="Date_Instances">Date Instances</span></h2>
<p>The JavaScript date is measured in milliseconds since midnight 01 January, 1970 UTC. A day holds 86,400,000 milliseconds. The JavaScript Date object range is -100,000,000 days to 100,000,000 days relative to 01 January, 1970 UTC.
</p><p>The JavaScript Date object provides uniform behavior across platforms.
</p><p>The JavaScript Date object supports a number of UTC (universal) methods, as well as local time methods. UTC, also known as Greenwich Mean Time (GMT), refers to the time as set by the World Time Standard. The local time is the time known to the computer where JavaScript is executed.
</p><p>A Date object contains a number representing a particular instant in time to within a millisecond. If the value of an argument is greater than its range or is a negative number, other stored values are modified accordingly. For example, if you specify 150 seconds, JavaScript redefines that number as two minutes and 30 seconds.
</p><p>If the number is NaN, the object does not represent a specific instant of time. If you pass no parameters to the Date object, it is initialized to the current time (UTC). A value must be given to the object before you can use it.
</p><p>The range of dates that can be represented in a Date object is approximately 285,616 years on either side of January 1, 1970.
</p><p>See Date and Time Calculations (JavaScript) for more information about how to use the Date object and related methods.
</p><p><br />
</p>
<h1><span class="mw-headline" id="Examples">Examples</span></h1>
<h2><span class="mw-headline" id="Several_ways_to_assign_dates">Several ways to assign dates</span></h2>
<p>The following examples show several ways to assign JavaScript dates:
</p>
<pre>today = new Date();
birthday = new Date("December 17, 1995 03:24:00");
birthday = new Date(1995,11,17);
birthday = new Date(1995,11,17,3,24,0);
</pre>
<h2><span class="mw-headline" id="Calculating_elapsed_time">Calculating elapsed time</span></h2>
<p>The following examples show how to determine the elapsed time between two JavaScript dates:	
</p>
<pre>// using static methods
var start = Date.now();
// the event you'd like to time goes here:
doSomethingForALongTime();
var end = Date.now();
var elapsed = end - start; // time in milliseconds
</pre>
<pre>// if you have Date objects
var start = new Date();
// the event you'd like to time goes here:
doSomethingForALongTime();
var end = new Date();
var elapsed = end.getTime() - start.getTime(); // time in milliseconds
</pre>
<pre>// if you want to test a function and get back its return
function printElapsedTime (fTest) {
  var nStartTime = Date.now(), vReturn = fTest(), nEndTime = Date.now();
  alert("Elapsed time: " + String(nEndTime - nStartTime) + " milliseconds");
  return vReturn;
}

yourFunctionReturn = printElapsedTime(yourFunction);
</pre>
<h2><span class="mw-headline" id="ISO_8601_formatted_dates">ISO 8601 formatted dates</span></h2>
<p><code>Date.toISOString()</code> is now supported, so you can use that.
</p><p>The following example demonstrates how to manually format a JavaScript date, in an ISO 8601 format using UTC:
</p>
<pre>/* use a function for the exact format desired... */
function ISODateString(d){
  function pad(n){return n&lt;10&#160;? '0'+n&#160;: n}
  return d.getUTCFullYear()+'-'
    + pad(d.getUTCMonth()+1)+'-'
    + pad(d.getUTCDate())+'T'
    + pad(d.getUTCHours())+':'
    + pad(d.getUTCMinutes())+':'
    + pad(d.getUTCSeconds())+'Z'
}
var d = new Date();
console.log(ISODateString(d)); // prints something like 2009-09-28T19:03:12Z
</pre>
<h1><span class="mw-headline" id="Properties">Properties</span></h1>
<dl><dt><a href="/w/index.php?title=constructor_property&amp;action=edit&amp;redlink=1" class="new" title="constructor property (page does not exist)">constructor property</a></dt>
<dd> Specifies the function that creates an object.</dd>
<dt><a href="/w/index.php?title=prototype_Property&amp;action=edit&amp;redlink=1" class="new" title="prototype Property (page does not exist)">prototype Property</a></dt>
<dd> Returns a reference to the prototype for a class of objects.</dd></dl>
<p>Properties inherited from <a href="/w/index.php?title=JS/Function&amp;action=edit&amp;redlink=1" class="new" title="JS/Function (page does not exist)">Function</a>
</p>
<ul><li> <a href="/w/index.php?title=arity&amp;action=edit&amp;redlink=1" class="new" title="arity (page does not exist)">arity</a></li>
<li> <a href="/w/index.php?title=caller&amp;action=edit&amp;redlink=1" class="new" title="caller (page does not exist)">caller</a></li>
<li> <a href="/w/index.php?title=constructor&amp;action=edit&amp;redlink=1" class="new" title="constructor (page does not exist)">constructor</a></li>
<li> <a href="/w/index.php?title=length&amp;action=edit&amp;redlink=1" class="new" title="length (page does not exist)">length</a></li>
<li> <a href="/w/index.php?title=name&amp;action=edit&amp;redlink=1" class="new" title="name (page does not exist)">name</a></li></ul>
<p><i><b>Implementation Note:</b> Transclude property descriptions from child pages. For each ancestor listed in the "Inherits from" of the Overview Table, there should be a generated list of property links.</i>
</p>
<h1><span class="mw-headline" id="Methods">Methods</span></h1>
<dl><dt><a href="/w/index.php?title=JS/Date/now&amp;action=edit&amp;redlink=1" class="new" title="JS/Date/now (page does not exist)">now</a></dt>
<dd> Returns the numeric value corresponding to the current time.</dd>
<dt><a href="/w/index.php?title=JS/Date/parse&amp;action=edit&amp;redlink=1" class="new" title="JS/Date/parse (page does not exist)">parse</a></dt>
<dd> Parses a string representation of a JavaScript date, and returns the number of milliseconds since January 1, 1970, 00:00:00, local time.</dd>
<dt><a href="/w/index.php?title=JS/Date/UTC&amp;action=edit&amp;redlink=1" class="new" title="JS/Date/UTC (page does not exist)">UTC</a></dt>
<dd> Accepts the same parameters as the longest form of the constructor, and returns the number of milliseconds in a JavaScript Date object since January 1, 1970, 00:00:00, universal time.</dd></dl>
<p>Methods inherited from <a href="/w/index.php?title=JS/Function&amp;action=edit&amp;redlink=1" class="new" title="JS/Function (page does not exist)">Function</a>:
</p>
<ul><li> <a href="/w/index.php?title=JS/Function/apply&amp;action=edit&amp;redlink=1" class="new" title="JS/Function/apply (page does not exist)">apply</a></li>
<li> <a href="/w/index.php?title=JS/Function/call&amp;action=edit&amp;redlink=1" class="new" title="JS/Function/call (page does not exist)">call</a></li>
<li> <a href="/w/index.php?title=JS/Function/toSource&amp;action=edit&amp;redlink=1" class="new" title="JS/Function/toSource (page does not exist)">toSource</a></li>
<li> <a href="/w/index.php?title=JS/Function/toString&amp;action=edit&amp;redlink=1" class="new" title="JS/Function/toString (page does not exist)">toString</a></li></ul>
<p><i><b>Implementation Note:</b> Transclude method descriptions from child pages. For each ancestor listed in the "Inherits from" of the Overview Table, there should be a generated list of method links.</i>
</p><p><br />
</p>
<h1><span class="mw-headline" id="Instances">Instances</span></h1>
<p>Some correct and coherent explanation goes here.
</p>
<h2><span class="mw-headline" id="Instance_Properties">Instance Properties</span></h2>
<dl><dt>constructor</dt>
<dd> Returns the function that created an instance. This is the Date constructor by default.</dd></dl>
<p>Properties inherited from <a href="/w/index.php?title=JS/Object&amp;action=edit&amp;redlink=1" class="new" title="JS/Object (page does not exist)">Object</a>:
</p>
<ul><li> <a href="/w/index.php?title=constructor&amp;action=edit&amp;redlink=1" class="new" title="constructor (page does not exist)">constructor</a></li></ul>
<p><i><b>Implementation Note:</b> Transclude property descriptions from child pages. There should be a generated list of property links for items inherited by instances from Object..</i>
</p>
<h2><span class="mw-headline" id="Instance_Methods">Instance Methods</span></h2>
<dl><dt>getDate</dt>
<dd> Returns the day of the month (1-31) for the specified date according to local time.</dd>
<dt>getDay</dt>
<dd> Returns the day of the week (0-6) for the specified date according to local time.</dd>
<dt>getYear</dt>
<dd> Deprecated. Returns the year (usually 2-3 digits) in the specified date according to local time. Use getFullYear instead.</dd>
<dt>toJSON </dt>
<dd> Requires JavaScript 1.8.5. Returns a string encapsulating the Date object in JSON format.</dd>
<dt> toLocaleFormat</dt>
<dd> Non-standard. Converts a date to a string, using a format string.</dd></dl>
<p>Methods inherited from <a href="/w/index.php?title=JS/Object&amp;action=edit&amp;redlink=1" class="new" title="JS/Object (page does not exist)">Object</a>:
</p>
<ul><li> <a href="/w/index.php?title=toLocaleString&amp;action=edit&amp;redlink=1" class="new" title="toLocaleString (page does not exist)">toLocaleString</a></li></ul>
<p><br />
<i><b>Implementation Note:</b> Transclude method descriptions from child pages. There should be a generated list of method links for items inherited by instances from Object. Provide distinctive styling for "Deprecated", "Requires JavaScript </i>version<i>", and "Non-standard. Items with these flags should be called out in the Browser Compatibility table.</i>
</p>
<h1><span class="mw-headline" id="Notes">Notes</span></h1>
<h1><span class="mw-headline" id="Specifications">Specifications</span></h1>
<table class="wikitable">

<tr>
<th> Specification </th>
<th> Status </th>
<th> Relevant changes
</th></tr>
<tr>
<td>ECMA-262, 5.1 edition] </td>
<td>&#160;??? </td>
<td>
</td></tr>
</table>
<h1><span class="mw-headline" id="Browser_compatibility">Browser compatibility</span></h1>
<h2><span class="mw-headline" id="Desktop">Desktop</span></h2>
<div id="compat-desktop">
  <table class="compat-table">
       <tr>
        <th>Feature</th>
        <th>Chrome</th>
        <th>Firefox (Gecko)</th>
        <th>Internet Explorer</th>
        <th>Opera</th>
        <th>Safari</th>
      </tr>
      <tr>
        <td>Basic support</td>
        <td>5.0</td>
        <td><a href="/w/index.php?title=Template:CompatGeckoDesktop(%221%22)&amp;action=edit&amp;redlink=1" class="new" title="Template:CompatGeckoDesktop(&quot;1&quot;) (page does not exist)">Template:CompatGeckoDesktop("1")</a></td>
        <td>5.5</td>
        <td>7.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>
<h2><span class="mw-headline" id="Mobile">Mobile</span></h2>
<div id="compat-mobile">
  <table class="compat-table">
      <tr>
        <th>Feature</th>
        <th>Android</th>
        <th>Firefox Mobile (Gecko)</th>
        <th>IE Phone</th>
        <th>Opera Mobile</th>
        <th>Safari Mobile</th>
      </tr>
      <tr>
        <td>Basic support</td>
        <td>1.0</td>
        <td><a href="/w/index.php?title=Template:CompatGeckoMobile(%221%22)&amp;action=edit&amp;redlink=1" class="new" title="Template:CompatGeckoMobile(&quot;1&quot;) (page does not exist)">Template:CompatGeckoMobile("1")</a></td>
        <td>6.0</td>
        <td>6.0</td>
        <td>1.0</td>
      </tr>
  </table>
</div>
<h1><span class="mw-headline" id="See_also">See also</span></h1>
<h2><span class="mw-headline" id="Reference">Reference</span></h2>
<ul><li> <a href="/w/index.php?title=JavaScript_Objects&amp;action=edit&amp;redlink=1" class="new" title="JavaScript Objects (page does not exist)">JavaScript Objects</a></li>
<li> <a href="/w/index.php?title=Formatting_Date_and_Time_Strings_(JavaScript)&amp;action=edit&amp;redlink=1" class="new" title="Formatting Date and Time Strings (JavaScript) (page does not exist)">Formatting Date and Time Strings (JavaScript)</a></li>
<li> <a href="/w/index.php?title=new_Operator_(JavaScript)&amp;action=edit&amp;redlink=1" class="new" title="new Operator (JavaScript) (page does not exist)">new Operator (JavaScript)</a></li>
<li> <a href="/w/index.php?title=var_Statement_(JavaScript)&amp;action=edit&amp;redlink=1" class="new" title="var Statement (JavaScript) (page does not exist)">var Statement (JavaScript)</a></li></ul>
<h2><span class="mw-headline" id="Tutorial">Tutorial</span></h2>
<ul><li> <a href="/w/index.php?title=Working_with_Dates_and_Time_in_JavaScript&amp;action=edit&amp;redlink=1" class="new" title="Working with Dates and Time in JavaScript (page does not exist)">Working with Dates and Time in JavaScript</a></li></ul>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:202-0!*!0!!*!*!*!esi=1 and timestamp 20150731181521 and revision id 739
 -->
