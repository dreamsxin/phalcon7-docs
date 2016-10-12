Interface **Phalcon\\Annotations\\AdapterInterface**
====================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/annotations/adapterinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Annotations\\AdapterInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Annotations\\Reflection <Phalcon_Annotations_Reflection>`  **read** (*string* $key)

Read parsed annotations



abstract public  **write** (*string* $key, :doc:`Phalcon\\Annotations\\Reflection <Phalcon_Annotations_Reflection>` $data)

Write parsed annotations



abstract public  **setReader** (:doc:`Phalcon\\Annotations\\ReaderInterface <Phalcon_Annotations_ReaderInterface>` $reader)

Sets the annotations parser



abstract public :doc:`Phalcon\\Annotations\\ReaderInterface <Phalcon_Annotations_ReaderInterface>`  **getReader** ()

Returns the annotation reader



abstract public :doc:`Phalcon\\Annotations\\Reflection <Phalcon_Annotations_Reflection>`  **get** (*string|object* $className)

Parses or retrieves all the annotations found in a class



abstract public *array*  **getMethods** (*string* $className)

Returns the annotations found in all the class' methods



abstract public :doc:`Phalcon\\Annotations\\Collection <Phalcon_Annotations_Collection>`  **getMethod** (*string* $className, *string* $methodName)

Returns the annotations found in a specific method



abstract public *array*  **getProperties** (*string* $className)

Returns the annotations found in all the class' methods



abstract public :doc:`Phalcon\\Annotations\\Collection <Phalcon_Annotations_Collection>`  **getProperty** (*string* $className, *string* $propertyName)

Returns the annotations found in a specific property



