Abstract class **Phalcon\\Logger**
==================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/logger.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Logger is a component whose purpose is create logs using different backends via adapters, generating options, formats and filters also implementing transactions.  

.. code-block:: php

    <?php

    $logger = new Phalcon\Logger\Adapter\File("app/logs/test.log");
    $logger->log("This is a message");
    $logger->log("This is an error", Phalcon\Logger::ERROR);
    $logger->error("This is another error");



Constants
---------

*integer* **SPECIAL**

*integer* **CUSTOM**

*integer* **DEBUG**

*integer* **INFO**

*integer* **NOTICE**

*integer* **WARNING**

*integer* **ERROR**

*integer* **ALERT**

*integer* **CRITICAL**

*integer* **EMERGENCE**

*integer* **EMERGENCY**

