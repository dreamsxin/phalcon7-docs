日期助手（Date Helper）
========================

Phalcon中提供了 :code:`Phalcon\Date` 日期助手类，让你更方便的处理日期数据。

日期验证（Verify Date）
-----------------------

.. code-block:: php

    <?php

    $ret = Phalcon\Date::valid('2012-01-22 11:00:00', 'Y-m-d H:i:s');

日期格式化（Date Format）
-------------------------
根据需要的单位返回日期：

.. code-block:: php

    <?php

    $span = Phalcon\Date::span(60, 182, 'minutes,seconds');		// array('minutes' => 2, 'seconds' => 2)
    $span = Phalcon\Date::span(60, 182, array('minutes', 'seconds'));	// array('minutes' => 2, 'seconds' => 2)
    $span = Phalcon\Date::fuzzy_span(time() - 120, time());		// "a few minutes"
    $span = Phalcon\Date::fuzzy_span2(60);				// "1 minutes"
    $time = Phalcon\Date::formatted_time('5 minutes ago');

模糊日期（Fuzzy Date）
----------------------
显示更容易理解的时间值：

.. code-block:: php

    <?php

    $span = Phalcon\Date::fuzzy_span(time() - 10); // "moments ago"
    $span = Phalcon\Date::fuzzy_span(time() - 120, time()); // "a few minutes"

    $span = Phalcon\Date::fuzzy_span2(60); // "1 minutes"

