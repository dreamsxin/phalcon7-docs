Abstract class **Phalcon\\Date**
================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/date.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Provides utilities to work with dates


Constants
---------

*integer* **YEAR**

*integer* **MONTH**

*integer* **WEEK**

*integer* **DAY**

*integer* **HOUR**

*integer* **MINUTE**

*string* **MONTHS_LONG**

*string* **MONTHS_SHORT**

Methods
-------

public static *int*  **offset** (*string* $remote, [*string* $local], [*unknown* $now])

Returns the offset (in seconds) between two time zones. Use this to display dates to users in different time zones. $seconds = Phalcon\\Date::offset('America/Chicago', 'GMT');



public static *array*  **seconds** ([*int* $step], [*int* $start], [*int* $end])

Number of seconds in a minute, incrementing by a step. Typically used as a shortcut for generating a list that can used in a form. $seconds = Phalcon\\Date::seconds(); // 00, 01, 02, 03, ..., 58, 59



public static *array*  **minutes** ([*int* $step])

Number of minutes in an hour, incrementing by a step. Typically used as a shortcut for generating a list that can be used in a form. $minutes = Phalcon\\Date::minutes(); // 00, 05, 10, 15, ..., 50, 55



public static *array*  **hours** ([*int* $step], [*unknown* $long], [*int* $start])

Number of hours in a day. Typically used as a shortcut for generating a list that can be used in a form. $hours = Phalcon\\Date::hours(); // 01, 02, 03, ..., 10, 11, 12



public static *string*  **adjust** (*int* $hour, *string* $ampm)

Adjusts a non-24-hour number into a 24-hour number. $hour = Phalcon\\Date::adjust(3, 'pm'); // 15



public static *string*  **ampm** (*int* $hour)

Returns AM or PM, based on a given hour (in 24 hour format). $type = Phalcon\\Date::ampm(12); // PM $type = Phalcon\\Date::ampm(1);  // AM



public static *array*  **days** (*int* $month, [*int* $year])

Number of days in a given month and year. Typically used as a shortcut for generating a list that can be used in a form. Phalcon\\Date::days(4, 2010); // 1, 2, 3, ..., 28, 29, 30



public static *array*  **months** ([*string* $format])

Number of months in a year. Typically used as a shortcut for generating a list that can be used in a form. By default a mirrored array of $month_number => $month_number is returned Phalcon\\Date::months(); // aray(1 => 1, 2 => 2, 3 => 3, ..., 12 => 12) But you can customise this by passing in either PHALCON_DATE_MONTHS_LONG Phalcon\\Date::months(Phalcon\\Utils\\PHALCON_DATE_MONTHS_LONG); // array(1 => 'January', 2 => 'February', ..., 12 => 'December') Or PHALCON_DATE_MONTHS_SHORT Phalcon\\Date::months(Phalcon\\Date::PHALCON_DATE_MONTHS_SHORT); // array(1 => 'Jan', 2 => 'Feb', ..., 12 => 'Dec')



public static *array*  **years** ([*int* $start], [*int* $end])

Returns an array of years between a starting and ending year. By default, the the current year - 5 and current year + 5 will be used. Typically used as a shortcut for generating a list that can be used in a form. $years = Phalcon\\Date::years(2000, 2010); // 2000, 2001, ..., 2009, 2010



public static *string/array*  **span** (*int* $remote, [*int* $local], [*string* $output])

Returns time difference between two timestamps, in human readable format. If the second timestamp is not given, the current time will be used. Also consider using [Phalcon\\Date::fuzzy_span] when displaying a span. $span = Phalcon\\Date::span(60, 182, 'minutes,seconds'); // array('minutes' => 2, 'seconds' => 2) $span = Phalcon\\Date::span(60, 182, 'minutes'); // 2



public static *string/array*  **span2** (*unknown* $remote, [*string* $output])

Returns time, in human readable format. Also consider using [Phalcon\\Date::fuzzy_span2] when displaying a span. $span = Phalcon\\Date::span(182, 'minutes,seconds'); // array('minutes' => 3, 'seconds' => 2) $span = Phalcon\\Date::span(182, 'minutes'); // 3



public static *string*  **fuzzy_span** (*int* $timestamp, [*int* $local_timestamp])

Returns the difference between a time and now in a "fuzzy" way. Displaying a fuzzy time instead of a date is usually faster to read and understand. $span = Phalcon\\Date::fuzzy_span(time() - 10); // "moments ago" $span = Phalcon\\Date::fuzzy_span(time() + 20); // "in moments" A second parameter is available to manually set the "local" timestamp, however this parameter shouldn't be needed in normal usage and is only included for unit tests



public static *string*  **fuzzy_span2** (*int* $timestamp, [*string* $output])

Returns the time in a "fuzzy" way. Displaying a fuzzy time instead of a date is usually faster to read and understand. $span = Phalcon\\Date::fuzzy_span2(60); // "1 minutes" $span = Phalcon\\Date::fuzzy_span2(10); // "10 seconds" A second parameter is available to manually set the "local" timestamp, however this parameter shouldn't be needed in normal usage and is only included for unit tests



public static *int*  **unix2dos** ([*int* $timestamp])

Converts a UNIX timestamp to DOS format. There are very few cases where this is needed, but some binary formats use it (eg: zip files.) $dos = Phalcon\\Date::unix2dos($unix);



public static *int*  **dos2unix** ([*int* $timestamp])

Converts a DOS timestamp to UNIX format.There are very few cases where this is needed, but some binary formats use it (eg: zip files.) $unix = Phalcon\\Date::dos2unix($dos);



public static *string*  **formatted_time** ([*string* $datetime_str], [*string* $timestamp_format], [*string* $timezone])

Returns a date/time string with the specified timestamp format $time = Phalcon\\Date::formatted_time('5 minutes ago');



public static *string*  **valid** (*unknown* $date, [*unknown* $format])

Returns a date/time string with the specified timestamp format $ret = Phalcon\\Date::valid('2012-01-22'); $ret = Phalcon\\Date::valid('2012-01-22 11:00:00', 'Y-m-d H:i:s');



