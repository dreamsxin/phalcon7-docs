Class **Phalcon\\Http\\Parser**
===============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/parser.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    $parser = new Phalcon\Http\Parser(Phalcon\Http\Parser::TYPE_BOTH);
      $result = $parser->execute($body);



Constants
---------

*integer* **TYPE_REQUEST**

*integer* **HTTP_RESPONSE**

*integer* **TYPE_BOTH**

Methods
-------

public  **__construct** ([*int* $type])

Phalcon\\Http\\Parser constructor



public *array|boolean $result*  **execute** (*unknown* $body, [*unknown* $output])

parse



public *array*  **parseCookie** (*string* $str)

parse cookies



