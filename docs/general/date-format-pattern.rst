.. _date-format-pattern:

===================
Date Format/Pattern
===================

.. note:: this information was copied from |elastic-date-format| 

.. |elastic-date-format| raw:: html

   <a href="https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-daterange-aggregation.html#date-format-pattern" target="_blank">Elasticsearch Date Format/Pattern</a>

All ASCII letters are reserved as format pattern letters, which are defined as follows:

.. list-table::
   :widths: 15 15 15 55
   :header-rows: 1

   * - Stymbol
     - Meaning
     - Presentation
     - Examples
   * - G
     - era
     - text
     - AD; Anno Domini; A
   * - u
     - year
     - year
     - 2004; 04
   * - y
     - year-of-era
     - year
     - 2004; 04
   * - D
     - day-of-year
     - number
     - 189
   * - M/L
     - month-of-year
     - number/text
     - 7; 07; Jul; July; J
   * - d
     - day-of-month
     - number
     - 10
   * - Q/q
     - quarter-of-year
     - number/text
     - 3; 03; Q3; 3rd quarter
   * - Y
     - week-based-year
     - year
     - 1996; 96
   * - w
     - week-of-week-based-year
     - number
     - 27
   * - W
     - week-of-month
     - number
     - 4
   * - E
     - day-of-week
     - text
     - Tue; Tuesday; T
   * - e/c
     - localized day-of-week
     - number/text
     - 2; 02; Tue; Tuesday; T
   * - F
     - week-of-month
     - number
     - 3
   * - a
     - am-pm-of-day
     - text
     - PM
   * - h
     - clock-hour-of-am-pm (1-12)
     - number
     - 12
   * - K
     - hour-of-am-pm (0-11)
     - number
     - 0
   * - k
     - clock-hour-of-am-pm (1-24)
     - number
     - 0
   * - H
     - hour-of-day (0-23)
     - number
     - 0
   * - m
     - minute-of-hour
     - number
     - 30
   * - s
     - second-of-minute
     - number
     - 55
   * - S
     - fraction-of-second
     - fraction
     - 978
   * - A
     - milli-of-day
     - number
     - 1234
   * - n
     - nano-of-second
     - number
     - 987654321
   * - N
     - nano-of-day
     - number
     - 1234000000
   * - V
     - time-zone ID
     - zone-id
     - America/Los_Angeles; Z; -08:30
   * - z
     - time-zone name
     - zone-name
     - Pacific Standard Time; PST
   * - O
     - localized zone-offset
     - offset-O
     - GMT+8; GMT+08:00; UTC-08:00;
   * - X
     - zone-offset Z for zero
     - offset-X
     - Z; -08; -0830; -08:30; -083015; -08:30:15;
   * - x
     - zone-offset
     - offset-x
     - +0000; -08; -0830; -08:30; -083015; -08:30:15;
   * - Z
     - zone-offset
     - offset-Z
     - +0000; -0800; -08:00;
   * - p
     - pad next
     - pad modifier
     - 1
   * - '
     - escape for text
     - delimiter
     - ''
   * - single quote
     - literal
     - '
     - [
   * - optional section start
     - ]
     - optional section end
     - #
   * - reserved for future use
     - {
     - reserved for future use
     - }
     
The count of pattern letters determines the format.

Text
====
The text style is determined based on the number of pattern letters used. Less than 4 pattern letters will use the short form. Exactly 4 pattern letters will use the full form. Exactly 5 pattern letters will use the narrow form. Pattern letters L, c, and q specify the stand-alone form of the text styles. 

Number
======
If the count of letters is one, then the value is output using the minimum number of digits and without padding. Otherwise, the count of digits is used as the width of the output field, with the value zero-padded as necessary. The following pattern letters have constraints on the count of letters. Only one letter of c and F can be specified. Up to two letters of d, H, h, K, k, m, and s can be specified. Up to three letters of D can be specified. 

Number/Text
===========
If the count of pattern letters is 3 or greater, use the Text rules above. Otherwise use the Number rules above. 

Fraction
========
Outputs the nano-of-second field as a fraction-of-second. The nano-of-second value has nine digits, thus the count of pattern letters is from 1 to 9. If it is less than 9, then the nano-of-second value is truncated, with only the most significant digits being output. 

Year
====
The count of letters determines the minimum field width below which padding is used. If the count of letters is two, then a reduced two digit form is used. For printing, this outputs the rightmost two digits. For parsing, this will parse using the base value of 2000, resulting in a year within the range 2000 to 2099 inclusive. If the count of letters is less than four (but not two), then the sign is only output for negative years as per SignStyle.NORMAL. Otherwise, the sign is output if the pad width is exceeded, as per SignStyle.EXCEEDS_PAD. 

ZoneId
======
This outputs the time-zone ID, such as Europe/Paris. If the count of letters is two, then the time-zone ID is output. Any other count of letters throws IllegalArgumentException. 

Zone names
==========
This outputs the display name of the time-zone ID. If the count of letters is one, two or three, then the short name is output. If the count of letters is four, then the full name is output. Five or more letters throws IllegalArgumentException. 

Offset X and x
==============
This formats the offset based on the number of pattern letters. One letter outputs just the hour, such as +01, unless the minute is non-zero in which case the minute is also output, such as +0130. Two letters outputs the hour and minute, without a colon, such as +0130. Three letters outputs the hour and minute, with a colon, such as +01:30. Four letters outputs the hour and minute and optional second, without a colon, such as +013015. Five letters outputs the hour and minute and optional second, with a colon, such as +01:30:15. Six or more letters throws IllegalArgumentException. Pattern letter X (upper case) will output Z when the offset to be output would be zero, whereas pattern letter x (lower case) will output +00, +0000, or +00:00. 

Offset O
========
This formats the localized offset based on the number of pattern letters. One letter outputs the short form of the localized offset, which is localized offset text, such as GMT, with hour without leading zero, optional 2-digit minute and second if non-zero, and colon, for example GMT+8. Four letters outputs the full form, which is localized offset text, such as GMT, with 2-digit hour and minute field, optional second field if non-zero, and colon, for example GMT+08:00. Any other count of letters throws IllegalArgumentException. 

Offset Z
========
This formats the offset based on the number of pattern letters. One, two or three letters outputs the hour and minute, without a colon, such as +0130. The output will be +0000 when the offset is zero. Four letters outputs the full form of localized offset, equivalent to four letters of Offset-O. The output will be the corresponding localized offset text if the offset is zero. Five letters outputs the hour, minute, with optional second if non-zero, with colon. It outputs Z if the offset is zero. Six or more letters throws IllegalArgumentException. 

Optional section
================
The optional section markers work exactly like calling DateTimeFormatterBuilder.optionalStart() and DateTimeFormatterBuilder.optionalEnd(). 

Pad modifier
============
Modifies the pattern that immediately follows to be padded with spaces. The pad width is determined by the number of pattern letters. This is the same as calling DateTimeFormatterBuilder.padNext(int). 

For example, ppH outputs the hour-of-day padded on the left with spaces to a width of 2.

Any unrecognized letter is an error. Any non-letter character, other than [, ], {, }, # and the single quote will be output directly. Despite this, it is recommended to use single quotes around all characters that you want to output directly to ensure that future changes do not break your application.