---
title: Summary
todo_broken_links:
  note: 'During import MediaWiki could not find the following links, please fix and adjust this list.'
  links:
    - JS/Function
    - 'constructor property'
    - 'prototype Property'
    - arity
    - caller
    - constructor
    - length
    - name
    - JS/Date/now
    - JS/Date/parse
    - JS/Date/UTC
    - JS/Function/apply
    - JS/Function/call
    - JS/Function/toSource
    - JS/Function/toString
    - JS/Object
    - toLocaleString
    - 'JavaScript Objects'
    - 'Formatting Date and Time Strings (JavaScript)'
    - 'new Operator (JavaScript)'
    - 'var Statement (JavaScript)'
    - 'Working with Dates and Time in JavaScript'
    - 'Template:CompatGeckoDesktop("1")'
    - 'Template:CompatGeckoMobile("1")'
uri: 'WPD:Example Pages/JavaScript Object'

---
JavaScript `Date` objects let you work with dates and times.

Enables basic storage and retrieval of dates and times.

# Overview table

||
|Inherits from|[Function](/w/index.php?title=JS/Function&action=edit&redlink=1) (can be multiple links here)|
|Descendents|any children|

# Constructor syntax

    new Date()
    new Date(dateVal)
    new Date(year, month, day [, hour, minute, second, millisecond])

***Implementation Note:** link from the syntax block to the individual parameters; if possible, autogenerate the constructor syntax.*

## Parameters

dateVal
:   If an integer value, it represents the number of milliseconds since 1 January 1970 00:00:00 UTC (Unix Epoch). If a string, dateVal is parsed according to the rules in Formatting Date and Time Strings (JavaScript). In Microsoft Internet Explorer, the *dateVal* argument can also be a VT\_DATE value as returned from some ActiveX objects.
year
:   Required. Integer value representing the year. For compatibility (in order to avoid the Y2K problem), you should always specify the year in full; use 1998, rather than 98.
month
:   Required. Integer value representing the month, beginning with 0 for January to 11 for December.
day
:   Required. Integer value representing the day of the month (1-31).
hour
:   Optional. Integer value representing the hour of the day (0-23).
minute
:   Optional. Integer value representing the minute segment (0-59) of a time reading.
second
:   Optional. Integer value representing the seconds segment (0-59) of a time reading.
millisecond
:   Optional. Integer value representing the millisecond segment (0-999) of a time reading.

# Usage

## Constructor

Note: Note that JavaScript Date objects can only be instantiated by calling JavaScript Date as a constructor: calling it as a regular function (i.e. without the new operator) will return a string rather than a Date object; unlike other JavaScript object types, JavaScript Date objects have no literal syntax.

If you supply no arguments, the constructor creates a JavaScript Date object for today's date and time according to local time. If you supply some arguments but not others, the missing arguments are set to 0. If you supply any arguments, you must supply at least the year, month, and day. You can omit the hours, minutes, seconds, and milliseconds.

Invoking JavaScript Date in a non-constructor context (i.e., without the new operator) will return a string representing the current time.

## Date Instances

The JavaScript date is measured in milliseconds since midnight 01 January, 1970 UTC. A day holds 86,400,000 milliseconds. The JavaScript Date object range is -100,000,000 days to 100,000,000 days relative to 01 January, 1970 UTC.

The JavaScript Date object provides uniform behavior across platforms.

The JavaScript Date object supports a number of UTC (universal) methods, as well as local time methods. UTC, also known as Greenwich Mean Time (GMT), refers to the time as set by the World Time Standard. The local time is the time known to the computer where JavaScript is executed.

A Date object contains a number representing a particular instant in time to within a millisecond. If the value of an argument is greater than its range or is a negative number, other stored values are modified accordingly. For example, if you specify 150 seconds, JavaScript redefines that number as two minutes and 30 seconds.

If the number is NaN, the object does not represent a specific instant of time. If you pass no parameters to the Date object, it is initialized to the current time (UTC). A value must be given to the object before you can use it.

The range of dates that can be represented in a Date object is approximately 285,616 years on either side of January 1, 1970.

See Date and Time Calculations (JavaScript) for more information about how to use the Date object and related methods.

# Examples

## Several ways to assign dates

The following examples show several ways to assign JavaScript dates:

    today = new Date();
    birthday = new Date("December 17, 1995 03:24:00");
    birthday = new Date(1995,11,17);
    birthday = new Date(1995,11,17,3,24,0);

## Calculating elapsed time

The following examples show how to determine the elapsed time between two JavaScript dates:

    // using static methods
    var start = Date.now();
    // the event you'd like to time goes here:
    doSomethingForALongTime();
    var end = Date.now();
    var elapsed = end - start; // time in milliseconds

    // if you have Date objects
    var start = new Date();
    // the event you'd like to time goes here:
    doSomethingForALongTime();
    var end = new Date();
    var elapsed = end.getTime() - start.getTime(); // time in milliseconds

    // if you want to test a function and get back its return
    function printElapsedTime (fTest) {
      var nStartTime = Date.now(), vReturn = fTest(), nEndTime = Date.now();
      alert("Elapsed time: " + String(nEndTime - nStartTime) + " milliseconds");
      return vReturn;
    }

    yourFunctionReturn = printElapsedTime(yourFunction);

## ISO 8601 formatted dates

`Date.toISOString()` is now supported, so you can use that.

The following example demonstrates how to manually format a JavaScript date, in an ISO 8601 format using UTC:

    /* use a function for the exact format desired... */
    function ISODateString(d){
      function pad(n){return n<10 ? '0'+n : n}
      return d.getUTCFullYear()+'-'
        + pad(d.getUTCMonth()+1)+'-'
        + pad(d.getUTCDate())+'T'
        + pad(d.getUTCHours())+':'
        + pad(d.getUTCMinutes())+':'
        + pad(d.getUTCSeconds())+'Z'
    }
    var d = new Date();
    console.log(ISODateString(d)); // prints something like 2009-09-28T19:03:12Z

# Properties

[constructor property](/w/index.php?title=constructor_property&action=edit&redlink=1)
:   Specifies the function that creates an object.
[prototype Property](/w/index.php?title=prototype_Property&action=edit&redlink=1)
:   Returns a reference to the prototype for a class of objects.

Properties inherited from [Function](/w/index.php?title=JS/Function&action=edit&redlink=1)

-   [arity](/w/index.php?title=arity&action=edit&redlink=1)
-   [caller](/w/index.php?title=caller&action=edit&redlink=1)
-   [constructor](/w/index.php?title=constructor&action=edit&redlink=1)
-   [length](/w/index.php?title=length&action=edit&redlink=1)
-   [name](/w/index.php?title=name&action=edit&redlink=1)

***Implementation Note:** Transclude property descriptions from child pages. For each ancestor listed in the "Inherits from" of the Overview Table, there should be a generated list of property links.*

# Methods

[now](/w/index.php?title=JS/Date/now&action=edit&redlink=1)
:   Returns the numeric value corresponding to the current time.
[parse](/w/index.php?title=JS/Date/parse&action=edit&redlink=1)
:   Parses a string representation of a JavaScript date, and returns the number of milliseconds since January 1, 1970, 00:00:00, local time.
[UTC](/w/index.php?title=JS/Date/UTC&action=edit&redlink=1)
:   Accepts the same parameters as the longest form of the constructor, and returns the number of milliseconds in a JavaScript Date object since January 1, 1970, 00:00:00, universal time.

Methods inherited from [Function](/w/index.php?title=JS/Function&action=edit&redlink=1):

-   [apply](/w/index.php?title=JS/Function/apply&action=edit&redlink=1)
-   [call](/w/index.php?title=JS/Function/call&action=edit&redlink=1)
-   [toSource](/w/index.php?title=JS/Function/toSource&action=edit&redlink=1)
-   [toString](/w/index.php?title=JS/Function/toString&action=edit&redlink=1)

***Implementation Note:** Transclude method descriptions from child pages. For each ancestor listed in the "Inherits from" of the Overview Table, there should be a generated list of method links.*

# Instances

Some correct and coherent explanation goes here.

## Instance Properties

constructor
:   Returns the function that created an instance. This is the Date constructor by default.

Properties inherited from [Object](/w/index.php?title=JS/Object&action=edit&redlink=1):

-   [constructor](/w/index.php?title=constructor&action=edit&redlink=1)

***Implementation Note:** Transclude property descriptions from child pages. There should be a generated list of property links for items inherited by instances from Object..*

## Instance Methods

getDate
:   Returns the day of the month (1-31) for the specified date according to local time.
getDay
:   Returns the day of the week (0-6) for the specified date according to local time.
getYear
:   Deprecated. Returns the year (usually 2-3 digits) in the specified date according to local time. Use getFullYear instead.
toJSON
:   Requires JavaScript 1.8.5. Returns a string encapsulating the Date object in JSON format.
 toLocaleFormat
:   Non-standard. Converts a date to a string, using a format string.

Methods inherited from [Object](/w/index.php?title=JS/Object&action=edit&redlink=1):

-   [toLocaleString](/w/index.php?title=toLocaleString&action=edit&redlink=1)

***Implementation Note:** Transclude method descriptions from child pages. There should be a generated list of method links for items inherited by instances from Object. Provide distinctive styling for "Deprecated", "Requires JavaScript*version*", and "Non-standard. Items with these flags should be called out in the Browser Compatibility table.*

# Notes

# Specifications

|Specification|Status|Relevant changes|
|:------------|:-----|:---------------|
|ECMA-262, 5.1 edition]| ???||

# Browser compatibility

## Desktop

|Feature|Chrome|Firefox (Gecko)|Internet Explorer|Opera|Safari|
|:------|:-----|:--------------|:----------------|:----|:-----|
|Basic support|5.0|[Template:CompatGeckoDesktop("1")](/w/index.php?title=Template:CompatGeckoDesktop(%221%22)&action=edit&redlink=1)|5.5|7.0|1.0|

## Mobile

|Feature|Android|Firefox Mobile (Gecko)|IE Phone|Opera Mobile|Safari Mobile|
|:------|:------|:---------------------|:-------|:-----------|:------------|
|Basic support|1.0|[Template:CompatGeckoMobile("1")](/w/index.php?title=Template:CompatGeckoMobile(%221%22)&action=edit&redlink=1)|6.0|6.0|1.0|

# See also

## Reference

-   [JavaScript Objects](/w/index.php?title=JavaScript_Objects&action=edit&redlink=1)
-   [Formatting Date and Time Strings (JavaScript)](/w/index.php?title=Formatting_Date_and_Time_Strings_(JavaScript)&action=edit&redlink=1)
-   [new Operator (JavaScript)](/w/index.php?title=new_Operator_(JavaScript)&action=edit&redlink=1)
-   [var Statement (JavaScript)](/w/index.php?title=var_Statement_(JavaScript)&action=edit&redlink=1)

## Tutorial

-   [Working with Dates and Time in JavaScript](/w/index.php?title=Working_with_Dates_and_Time_in_JavaScript&action=edit&redlink=1)
