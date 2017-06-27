事件（Events）
==============
Phalcon7 中几乎所有的组件都继承自 :doc:`Phalcon\\Di\\Injectable <../api/Phalcon_Di_Injectable>`，它们都可以通过 `attachEvent` 来设置对应事件的回调函数。

使用示例（Usage Example）
-------------------------
以下面示例中，我们使用 `attachEvent` 设置MySQL连接中产生的事件的回调函数：

.. code-block:: php

    <?php

    use Phalcon\Db\Adapter\Pdo\Mysql as DbAdapter;

    $connection = new DbAdapter(
        array(
            "host"     => "localhost",
            "username" => "root",
            "password" => "secret",
            "dbname"   => "invo"
        )
    );

    $connection->attachEvent('beforeExecutePrepare', function($event, $statement){
	
	});

    $connection->query("SELECT * FROM products p WHERE p.status = 1");

事件管理器（Events Manager）
----------------------------
此组件的目的是为了通过创建“钩子”拦截框架中大部分的组件操作。:doc:`了解更多 <events-manager>`