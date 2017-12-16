Class **Phalcon\\Storage\\Leveldb**
===================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/leveldb.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

public  **__construct** (*string* $path, [*string* $options])

Phalcon\\Storage\\Leveldb constructor



public *string*  **get** (*string* $key)

Returns the value for the given key or false



public *mixed*  **put** (*string* $key, *string* $value, [*array* $options])

Puts the value for the given key



public *mixed*  **write** (:doc:`Phalcon\\Storage\\Leveldb\\Writebatch <Phalcon_Storage_Leveldb_Writebatch>` $batch, [*array* $options])

Executes all of the operations added in the write batch



public *boolean*  **delete** (*string* $key, [*array* $options])

Deletes the given key



public :doc:`Phalcon\\Storage\\Leveldb\\Iterator <Phalcon_Storage_Leveldb_Iterator>`  **iterator** ()

Gets a new iterator for the db



public  **set** (*unknown* $key, *unknown* $value, [*array* $options])

...


