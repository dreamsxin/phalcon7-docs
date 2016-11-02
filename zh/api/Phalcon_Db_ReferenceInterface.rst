Interface **Phalcon\\Db\\ReferenceInterface**
=============================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/db/referenceinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Db\\ReferenceInterface initializer


Methods
-------

abstract public *string*  **getName** ()

Gets the index name



abstract public *string*  **getSchemaName** ()

Gets the schema where referenced table is



abstract public *string*  **getReferencedSchema** ()

Gets the schema where referenced table is



abstract public *array*  **getColumns** ()

Gets local columns which reference is based



abstract public *string*  **getReferencedTable** ()

Gets the referenced table



abstract public *array*  **getReferencedColumns** ()

Gets referenced columns



abstract public *string*  **getOnDelete** ()

Gets the referenced on delete



abstract public *string*  **getOnUpdate** ()

Gets the referenced on update



