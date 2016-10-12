Class **Phalcon\\Db\\Index**
============================

*implements* :doc:`Phalcon\\Db\\IndexInterface <Phalcon_Db_IndexInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/index.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Allows to define indexes to be used on tables. Indexes are a common way to enhance database performance. An index allows the database server to find and retrieve specific rows much faster than it could do without an index


Methods
-------

public  **__construct** (*string* $indexName, *array* $columns, [*string|null* $type])

Phalcon\\Db\\Index constructor



public *string*  **getName** ()

Gets the index name



public *array*  **getColumns** ()

Gets the columns that comprends the index



public *string*  **getType** ()

Gets the index type



public static :doc:`Phalcon\\Db\\IndexInterface <Phalcon_Db_IndexInterface>`  **__set_state** ([*array* $properties])

Restore a Phalcon\\Db\\Index object from export



