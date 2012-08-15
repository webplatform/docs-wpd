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
; Required. Integer value representing the day of the month (1-31).
;hour
; Optional. Integer value representing the hour of the day (0-23).
;minute
; Optional. Integer value representing the minute segment (0-59) of a time reading.
;second
; Optional. Integer value representing the seconds segment (0-59) of a time reading.
;millisecond
: Optional. Integer value representing the millisecond segment (0-999) of a time reading.

=Properties=

=Methods=

=Functions=

=Instances=

==Properties==

==Methods==

=Examples=

=Usage=

=Notes=

=Specifications=

=Browser compatibility=

=See also=