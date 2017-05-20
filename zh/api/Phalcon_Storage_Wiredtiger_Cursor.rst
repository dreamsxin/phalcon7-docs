Class **Phalcon\\Storage\\Wiredtiger_Cursor**
=============================================

*implements* Iterator, Traversable

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/wiredtiger_cursor.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Methods
-------

public  **__construct** (:doc:`Phalcon\\Storage\\Wiredtiger <Phalcon_Storage_Wiredtiger>` $db, *string* $uri, [*string* $config])

Phalcon\\Storage\\Wiredtiger\\Cursor constructor



public  **reconfigure** (*string* $config)

Reconfigure the cursor to overwrite the record



public *boolean*  **set** (*mixed* $key, *mixed* $value)

Sets data



public *boolean*  **sets** (*array* $data)

Sets data



public *mixed*  **get** (*mixed* $key)

Gets data



public *array*  **gets** (*array* $keys)

Gets multi value



public *boolean*  **delete** (*mixed* $key)

Delete data



public *mixed*  **current** ()

Gets current value



public *mixed*  **key** ()

Gets current key



public *boolean*  **next** ()

Moves cursor to next row



public *boolean*  **prev** ()

Moves cursor to prev row



public *mixed*  **rewind** ()

Rewinds cursor to it's beginning



public *mixed*  **last** ()

Rewinds cursor to it's last



public *mixed*  **valid** ()

Check whether has rows to fetch



public  **close** ()

Close the cursor



