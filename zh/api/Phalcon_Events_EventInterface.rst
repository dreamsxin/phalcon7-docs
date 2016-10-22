Interface **Phalcon\\Events\\EventInterface**
=============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/events/eventinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Events\\EventInterface initializer


Methods
-------

abstract public  **setType** (*unknown* $eventType)

Sets event type



abstract public  **getType** ()

Gets event type



abstract public  **setSource** (*unknown* $source)

Sets event source



abstract public  **getSource** ()

Gets event source



abstract public  **setData** (*unknown* $data)

Sets event data



abstract public  **getData** ()

Gets event data



abstract public  **setCancelable** (*unknown* $cancelable)

Sets event is cancelable



abstract public  **isCancelable** ()

Check whether the event is cancelable



abstract public  **stop** ()

Stops the event preventing propagation



abstract public  **isStopped** ()

Check whether the event is currently stopped



