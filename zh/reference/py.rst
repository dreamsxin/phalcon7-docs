Python执行器（Embedded Python）
===============================

执行 Python 代码：

.. code-block:: php

    <?php

    function test() {
        return 'Test';
    }

    $py = <<<EOT
    import phalcon

    print phalcon.call('test')
    print phalcon.call('sha1', ('tuple',))
    print phalcon.call('sha1', ['list'])
    EOT;

    Phalcon\Py::exec($py);

导入模块：

.. code-block:: php

    <?php

    $phalcon = Phalcon\Py::import('phalcon');
    Phalcon\Py::callFunction($phalcon, 'call', 'test');

调用对象方法：

.. code-block:: php

    <?php

    $list = Phalcon\Py::list([5,1,2,3,4]);
    Phalcon\Py::callMethod($list, 'sort');
