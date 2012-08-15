=Summary=
JavaScript <code>Date</code> objects let you work with dates and times. 

Enables basic storage and retrieval of dates and times.

=Constructor syntax=
 new Date()
 new Date(dateVal)
 new Date(year, month, day [, hour, minute, second, millisecond])

==Parameters==

;dateVal
: If an integer value, it represents the number of milliseconds since 1 January 1970 00:00:00 UTC (Unix Epoch). If a string, dateVal is parsed according to the rules in Formatting Date and Time Strings (JavaScript). In Microsoft Internet Explorer, the ''dateVal'' argument can also be a VT_DATE value as returned from some ActiveX objects.
;year
: Required. Integer value representing the year. For compatibility (in order to avoid the Y2K problem), you should always specify the year in full; use 1998, rather than 98.
;month
: Required. Integer value representing the month, beginning with 0 for January to 11 for December.
;day
: Required. Integer value representing the day of the month (1-31).
;hour
: Optional. Integer value representing the hour of the day (0-23).
;minute
: Optional. Integer value representing the minute segment (0-59) of a time reading.
;second
: Optional. Integer value representing the seconds segment (0-59) of a time reading.
;millisecond
: Optional. Integer value representing the millisecond segment (0-999) of a time reading.

==Usage==
Note: Note that JavaScript Date objects can only be instantiated by calling JavaScript Date as a constructor: calling it as a regular function (i.e. without the new operator) will return a string rather than a Date object; unlike other JavaScript object types, JavaScript Date objects have no literal syntax.

If you supply no arguments, the constructor creates a JavaScript Date object for today's date and time according to local time. If you supply some arguments but not others, the missing arguments are set to 0. If you supply any arguments, you must supply at least the year, month, and day. You can omit the hours, minutes, seconds, and milliseconds.

The JavaScript date is measured in milliseconds since midnight 01 January, 1970 UTC. A day holds 86,400,000 milliseconds. The JavaScript Date object range is -100,000,000 days to 100,000,000 days relative to 01 January, 1970 UTC.

The JavaScript Date object provides uniform behavior across platforms.

The JavaScript Date object supports a number of UTC (universal) methods, as well as local time methods. UTC, also known as Greenwich Mean Time (GMT), refers to the time as set by the World Time Standard. The local time is the time known to the computer where JavaScript is executed.

Invoking JavaScript Date in a non-constructor context (i.e., without the new operator) will return a string representing the current time.

=Examples=

=Properties=

=Methods=

=Functions=

=Instances=

==Properties==

==Methods==

=Usage=

=Notes=

=Specifications=

=Browser compatibility=

=See also=