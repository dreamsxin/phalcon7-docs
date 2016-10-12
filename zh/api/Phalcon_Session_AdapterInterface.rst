Interface **Phalcon\\Session\\AdapterInterface**
================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/session/adapterinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Session\\AdapterInterface initializer


Methods
-------

abstract public  **start** ()

Starts session, optionally using an adapter



abstract public  **setOptions** (*array* $options)

Sets session options



abstract public *array*  **getOptions** ()

Get internal options



abstract public *mixed*  **get** (*string* $index, [*mixed* $defaultValue])

Gets a session variable from an application context



abstract public  **set** (*unknown* $index, *unknown* $value)

Sets a session variables in an application context



abstract public  **sets** (*unknown* $data)

...


abstract public *boolean*  **has** (*string* $index)

Check whether a session variable is set in an application context



abstract public  **remove** (*string* $index)

Removes a session variable from an application context



abstract public *string*  **getId** ()

Returns active session id



abstract public *boolean*  **isStarted** ()

Check whether the session has been started



abstract public *boolean*  **destroy** ([*unknown* $session_id])

Destroys the active session



