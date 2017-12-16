Class **Phalcon\\Sync\\Event**
==============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/sync/event.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

public  **__construct** ([*string* $name], [*boolean* $manual], [*boolean* $prefire])

Phalcon\\Sync\\Event constructor



public *boolean*  **wait** ([*int* $wait])

Waits for an event object to fire



public *boolean*  **fire** ()

Lets a thread through that is waiting.  Lets multiple threads through that are waiting if the event object is 'manual'



public *boolean*  **reset** ()

Resets the event object state.  Only use when the event object is 'manual'



