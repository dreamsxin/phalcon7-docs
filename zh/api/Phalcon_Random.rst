Class **Phalcon\\Random**
=========================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/random.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

      $random = new \Phalcon\Random();
    
      // Random alnum string
      $alnum = $random->alnum();



Constants
---------

*integer* **COLOR_RGB**

*integer* **COLOR_RGBA**

Methods
-------

public  **alnum** ([*unknown* $len])

Generates a random alnum string 

.. code-block:: php

    <?php

      $random = new \Phalcon\Random();
      $alnum = $random->alnum();




public  **alpha** ([*unknown* $len])

Generates a random alpha string 

.. code-block:: php

    <?php

      $random = new \Phalcon\Random();
      $alpha = $random->alpha();




public  **hexdec** ([*unknown* $len])

Generates a random hexdec string 

.. code-block:: php

    <?php

      $random = new \Phalcon\Random();
      $hexdec = $random->hexdec();




public  **numeric** ([*unknown* $len])

Generates a random numeric string 

.. code-block:: php

    <?php

      $random = new \Phalcon\Random();
      $numeric = $random->numeric();




public  **nozero** ([*unknown* $len])

Generates a random nozero numeric string 

.. code-block:: php

    <?php

      $random = new \Phalcon\Random();
      $bytes = $random->nozero();




public  **color** ([*unknown* $type])

Generates a random color



