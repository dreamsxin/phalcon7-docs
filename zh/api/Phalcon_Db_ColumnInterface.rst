Interface **Phalcon\\Db\\ColumnInterface**
==========================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/columninterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Db\\ColumnInterface initializer


Methods
-------

abstract public *string*  **getSchemaName** ()

Returns schema's table related to column



abstract public *string*  **getName** ()

Returns column name



abstract public *int*  **getType** ()

Returns column type



abstract public *int*  **getSize** ()

Returns column size



abstract public *int*  **getScale** ()

Returns column scale



abstract public *boolean*  **isUnsigned** ()

Returns true if number column is unsigned



abstract public *boolean*  **isNotNull** ()

Not null



abstract public *boolean*  **isPrimary** ()

Column is part of the primary key?



abstract public *boolean*  **isAutoIncrement** ()

Auto-Increment



abstract public *boolean*  **isNumeric** ()

Check whether column have an numeric type



abstract public *boolean*  **isFirst** ()

Check whether column have first position in table



abstract public *string*  **getAfterPosition** ()

Check whether field absolute to position in table



abstract public *int*  **getBindType** ()

Returns the type of bind handling



