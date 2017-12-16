Class **Phalcon\\Storage\\Libmdbx**
===================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/libmdbx.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Constants
---------

*integer* **NOSUBDIR**

*integer* **NOSYNC**

*integer* **RDONLY**

*integer* **NOMETASYNC**

*integer* **WRITEMAP**

*integer* **MAPASYNC**

*integer* **NOTLS**

*integer* **NORDAHEAD**

*integer* **NOMEMINIT**

*integer* **REVERSEKEY**

*integer* **DUPSORT**

*integer* **INTEGERKEY**

*integer* **DUPFIXED**

*integer* **INTEGERDUP**

*integer* **REVERSEDUP**

*integer* **CREATE**

*integer* **NOOVERWRITE**

*integer* **NODUPDATA**

*integer* **CURRENT**

*integer* **RESERVE**

*integer* **APPEND**

*integer* **APPENDDUP**

*integer* **MULTIPLE**

*integer* **CP_COMPACT**

*integer* **SUCCESS**

*integer* **KEYEXIST**

*integer* **NOTFOUND**

*integer* **PAGE_NOTFOUND**

*integer* **CORRUPTED**

*integer* **PANIC**

*integer* **VERSION_MISMATCH**

*integer* **INVALID**

*integer* **MAP_FULL**

*integer* **DBS_FULL**

*integer* **READERS_FULL**

*integer* **TXN_FULL**

*integer* **CURSOR_FULL**

*integer* **PAGE_FULL**

*integer* **MAP_RESIZED**

*integer* **INCOMPATIBLE**

*integer* **BAD_RSLOT**

*integer* **BAD_TXN**

*integer* **BAD_VALSIZE**

*integer* **BAD_DBI**

*integer* **PROBLEM**

*integer* **LAST_ERRCODE**

Methods
-------

public  **__construct** (*string* $path, [*string* $name], [*int* $readers], [*int* $mapsize], [*unknown* $flags])

Phalcon\\Storage\\Libmdbx constructor



public  **begin** ([*unknown* $flags])

Create a transaction for use with the environment



public  **commit** ()

Commit all the operations of a transaction into the database



public  **renew** ()

Renew a read-only transaction



public  **reset** ()

Reset a read-only transaction



public *array*  **getAll** ()

Get all items from a database



public *string*  **get** (*string* $key)

Get items from a database



public *mixed*  **put** (*string* $key, *mixed* $value, [*unknown* $flags])

Store items into a database



public *boolean*  **del** (*unknown* $key)

Delete items from a database



public :doc:`Phalcon\\Storage\\Libmdbx\\Cursor <Phalcon_Storage_Libmdbx_Cursor>`  **cursor** ()

Create a cursor handle



public *boolean*  **copy** (*string* $path, [*int* $flags])

Copy an LIBMDBX environment to the specified path



public *boolean*  **drop** ([*unknown* $delete])

Empty or delete+close a database



public  **set** (*unknown* $key, *unknown* $value, [*unknown* $flags])

...


public  **delete** (*unknown* $key)

...


