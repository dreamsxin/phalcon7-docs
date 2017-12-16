Class **Phalcon\\Events\\Event**
================================

*implements* :doc:`Phalcon\\Events\\EventInterface <Phalcon_Events_EventInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/events/event.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class offers contextual information of a fired event in the EventsManager


Methods
-------

public  **__construct** (*string* $type, *object* $source, [*mixed* $data], [*boolean* $cancelable], [*unknown* $flag])

Phalcon\\Events\\Event constructor



public  **setName** (*string* $eventName)

Set the event's name



public *string*  **getName** ()

Returns the event's name



public  **setType** (*string* $eventType)

Set the event's type



public *string*  **getType** ()

Returns the event's type



public *object*  **setSource** (*unknown* $source)

Sets the event's source



public *object*  **getSource** ()

Returns the event's source



public  **setData** (*string* $data)

Set the event's data



public *mixed*  **getData** ()

Returns the event's data



public  **setCancelable** (*boolean* $cancelable)

Sets if the event is cancelable



public *boolean*  **isCancelable** ()

Check whether the event is cancelable



public *mixed*  **getFlag** ()

Returns the event's flag



public  **stop** ()

Stops the event preventing propagation



public  **isStopped** ()

Check whether the event is currently stopped



public  **getCancelable** ()

...


