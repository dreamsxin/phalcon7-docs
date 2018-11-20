注意事项（Notifications）
=========================
开发中容易犯的错误。

* 忘记释放变量

尽量使用 `PHALCON_MM` 系列宏定义。

* 对 PHP 传递进来的参数再次赋值

.. code-block:: c

	PHP_METHOD(Phalcon_Mvc_Application, handle){
		phalcon_fetch_params(1, 0, 1, &uri);
		// ...
		ZVAL_COPY_VALUE(&uri, &tmp);
	}
