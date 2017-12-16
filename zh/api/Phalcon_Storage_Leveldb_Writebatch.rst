Class **Phalcon\\Storage\\Leveldb\\Writebatch**
===============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/leveldb/writebatch.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

public *mixed*  **put** (*string* $key, *string* $value)

Adds a put operation for the given key and value to the write batch



public *boolean*  **delete** (*string* $key)

Adds a deletion operation for the given key to the write batch



public *boolean*  **clear** ()

Clears all of operations in the write batch



