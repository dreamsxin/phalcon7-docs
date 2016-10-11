Interface **Phalcon\\Annotations\\ReaderInterface**
===================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/annotations/readerinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Annotations\\ReaderInterface initializer


Methods
-------

abstract public *array*  **parse** (*string* $className)

Reads annotations from the class dockblocks, its methods and/or properties



abstract public static *array*  **parseDocBlock** (*string* $docBlock, [*unknown* $file], [*unknown* $line])

Parses a raw doc block returning the annotations found



