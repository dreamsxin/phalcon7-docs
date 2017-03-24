Class **Phalcon\\Storage\\Bloomfilter**
=======================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/storage/bloomfilter.c" class="btn btn-default btn-sm">Source on GitHub</a>`

This class defines bloomfilter entity and its description


Methods
-------

final public  **__construct** (*unknown* $filename, [*unknown* $seed], [*unknown* $maxItems], [*unknown* $falsePositive])

Phalcon\\Storage\\Bloomfilter constructor



public *boolean*  **add** (*string* $value)

Add value



public *boolean*  **check** (*string* $value)

Check value



public *boolean*  **reset** ()

Reset



public *boolean*  **save** ()

Save data to file



