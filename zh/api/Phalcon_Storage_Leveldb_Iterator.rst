Class **Phalcon\\Storage\\Leveldb\\Iterator**
=============================================

*implements* Iterator, Traversable, SeekableIterator

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/leveldb/iterator.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

final private  **__construct** ()

Phalcon\\Storage\\Leveldb\\Iterator constructor



public *string*  **current** ()

Return current element



public *string*  **key** ()

Returns the key of current element



public *boolean*  **next** ()

Moves forward to the next element



public *boolean*  **prev** ()

Moves backward to the previous element



public *boolean*  **rewind** ()

Rewinds back to the first element of the Iterator



public *boolean*  **last** ()

Moves to the last element of the Iterator



public *boolean*  **seek** (*unknown* $position)

Seeks to a given key in the Iterator if no such key it will point to nearest key



public *boolean*  **valid** ()

Checks if current position is valid



