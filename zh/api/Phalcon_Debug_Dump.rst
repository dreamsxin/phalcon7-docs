Class **Phalcon\\Debug\\Dump**
==============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/debug/dump.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Dumps information about a variable(s)  

.. code-block:: php

    <?php

        $foo = 123;
        echo (new \Phalcon\Debug\Dump())->variable($foo, "foo");

.. code-block:: php

    <?php

        $foo = "string";
        $bar = ["key" => "value"];
        $baz = new stdClass();
        echo (new \Phalcon\Debug\Dump())->variables($foo, $bar, $baz);



Methods
-------

public  **__construct** ([*unknown* $styles], [*unknown* $detailed])

Phalcon\\Debug\\Dump constructor



public  **all** ()

Alias of variables() method



public  **getStyle** (*unknown* $type)

Get style for type



public  **setStyles** ([*unknown* $styles])

Set styles for vars type



public  **output** (*unknown* $variable, [*unknown* $name], [*unknown* $tab])

Prepare an HTML string of information about a single variable.



public  **variable** (*unknown* $variable, [*unknown* $name])

Returns an HTML string of information about a single variable. 

.. code-block:: php

    <?php

        echo (new \Phalcon\Debug\Dump())->variable($foo, "foo");




public  **variables** ()

Returns an HTML string of debugging information about any number of variables, each wrapped in a "pre" tag. 

.. code-block:: php

    <?php

        $foo = "string";
        $bar = ["key" => "value"];
        $baz = new stdClass();
        echo (new \Phalcon\Debug\Dump())->variables($foo, $bar, $baz);




public  **one** (*unknown* $variable, [*unknown* $name])

...


public  **var** (*unknown* $variable, [*unknown* $name])

...


public  **vars** ()

...


