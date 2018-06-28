Class **Phalcon\\Date\\DateTime**
=================================

*extends* DateTime

*implements* DateTimeInterface

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/date/datetime.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

     $datetime = new \Phalcon\Date\DateTime();
     $start = $datetime->startOfDay();
     $end = $datetime->endOfDay();



Constants
---------

*string* **ATOM**

*string* **COOKIE**

*string* **ISO8601**

*string* **RFC822**

*string* **RFC850**

*string* **RFC1036**

*string* **RFC1123**

*string* **RFC7231**

*string* **RFC2822**

*string* **RFC3339**

*string* **RFC3339_EXTENDED**

*string* **RSS**

*string* **W3C**

Methods
-------

public  **__construct** (*unknown* $font)

Create a new instance



public *\DateTime*  **setDateTime** (*int* $year, *int* $month, *int* $day, *int* $hour, *int* $minute, [*int* $second])

Set the date and time all together



public *\DateTime*  **startOfDay** ()

Resets the time to 00:00:00



public *\DateTime*  **endOfDay** ()

Resets the time to 23:59:59



public *\DateTime*  **startOfMonth** ()

Resets the date to the first day of the month and the time to 00:00:00



public *\DateTime*  **endOfMonth** ()

Resets the date to end of the month and time to 23:59:59



public *\DateTime*  **startOfQuarter** ()

Resets the date to the first day of the quarter and the time to 00:00:00



public *\DateTime*  **endOfQuarter** ()

Resets the date to end of the quarter and time to 23:59:59



public *\DateTime*  **startOfYear** ()

Resets the date to the first day of the year and the time to 00:00:00



public *\DateTime*  **endOfYear** ()

Resets the date to end of the year and time to 23:59:59



public *\DateTime*  **startOfDecade** ()

Resets the date to the first day of the year and the time to 00:00:00



public *\DateTime*  **endOfDecade** ()

Resets the date to end of the decade and time to 23:59:59



public *\DateTime*  **startOfCentury** ()

Resets the date to the first day of the century and the time to 00:00:00



public *\DateTime*  **endOfCentury** ()

Resets the date to end of the century and time to 23:59:59



public *\DateTime*  **modifyYear** (*unknown* $year)

Add or Remove years from the instance



public *\DateTime*  **modifyQuarter** (*unknown* $quarter)

Add or Remove quarters from the instance



public *\DateTime*  **modifyMonth** (*unknown* $month)

Add or Remove months from the instance



public *\DateTime*  **modifyDay** (*unknown* $day)

Add or Remove days from the instance



public *\DateTime*  **modifyHour** (*unknown* $hour)

Add or Remove hours from the instance



public *\DateTime*  **modifyMinute** (*unknown* $minute)

Add or Remove minutes from the instance



public *\DateTime*  **modifySecond** (*unknown* $second)

Add or Remove seconds from the instance



public *string|int|\DateTimeZone*  **__get** (*unknown* $property)

Get a part of the Carbon object



public  **__wakeup** () inherited from DateTime

...


public static  **__set_state** () inherited from DateTime

...


public static  **createFromFormat** (*unknown* $format, *unknown* $time, [*unknown* $object]) inherited from DateTime

...


public static  **getLastErrors** () inherited from DateTime

...


public  **format** (*unknown* $format) inherited from DateTime

...


public  **modify** (*unknown* $modify) inherited from DateTime

...


public  **add** (*unknown* $interval) inherited from DateTime

...


public  **sub** (*unknown* $interval) inherited from DateTime

...


public  **getTimezone** () inherited from DateTime

...


public  **setTimezone** (*unknown* $timezone) inherited from DateTime

...


public  **getOffset** () inherited from DateTime

...


public  **setTime** (*unknown* $hour, *unknown* $minute, [*unknown* $second], [*unknown* $microseconds]) inherited from DateTime

...


public  **setDate** (*unknown* $year, *unknown* $month, *unknown* $day) inherited from DateTime

...


public  **setISODate** (*unknown* $year, *unknown* $week, [*unknown* $day]) inherited from DateTime

...


public  **setTimestamp** (*unknown* $unixtimestamp) inherited from DateTime

...


public  **getTimestamp** () inherited from DateTime

...


public  **diff** (*unknown* $object, [*unknown* $absolute]) inherited from DateTime

...


