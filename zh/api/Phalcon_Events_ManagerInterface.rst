Interface **Phalcon\\Events\\ManagerInterface**
===============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/events/managerinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Events\\ManagerInterface initializer


Methods
-------

abstract public  **attach** (*string* $eventType, *object* $handler)

Attach a listener to the events manager



abstract public  **detach** (*string* $type, *object* $handler)

Detach a listener from the events manager



abstract public  **detachAll** ([*string* $type])

Removes all events from the EventsManager



abstract public *mixed*  **fire** (*string* $eventType, *object* $source, [*mixed* $data])

Fires a event in the events manager causing that the acive listeners will be notified about it



abstract public *array*  **getListeners** (*string* $type, [*unknown* $full])

Returns all the attached listeners of a certain type



