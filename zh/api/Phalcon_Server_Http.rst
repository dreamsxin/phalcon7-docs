Class **Phalcon\\Server\\Http**
===============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/server/http.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    $server = new Phalcon\Server\Http('127.0.0.1', 8989);
      $server->start($application);



Methods
-------

public  **__construct** ([*array* $config])

Phalcon\\Http\\Server constructor



public  **start** (:doc:`Phalcon\\Application <Phalcon_Application>` $application)

Run the Server



