包含（requires）
================
Phalcon API 提供了 `phalcon_require` 函数实现 PHP 的 `require` 功能，在实际开发过程中，进程会在一个文件中包含另一个或者直接从另一个文件中返回一组数据。

实例（instance）
----------------
假如我们要实现如下 PHP 代码的功能：

.. code-block:: php

	$file = "config.php";
	$config = require($file);

在 Phalcon 中使用 API 实现起来也一样简单：

.. code-block:: php

	zval config = {};

	phalcon_require_ret(&config, "config.php");

内部实现（implementation）
--------------------------

.. code-block:: c

	// Check file exists
	if (VCWD_STAT(file_name, &file_sb) == 0) {
		// Whether it is a regular file
		if (S_ISREG(file_sb.st_mode)) {
			// Open file
			if (( fh.handle.fp = VCWD_FOPEN(file_name, "r") )) {
				fh.filename = file_name;
				fh.type = ZEND_HANDLE_FILENAME;
				fh.free_filename = 0;
				fh.opened_path = NULL;

				// Compile file
				op_array = zend_compile_file(&fh, ZEND_REQUIRE TSRMLS_CC);

				// Delete file handle
				zend_destroy_file_handle(&fh);

				// Check compile results
				if (op_array) {
					zval result;
					ZVAL_UNDEF(&result);

					// Access to compile the results
					zend_execute(op_array, &result);
					// result => $config

					ZVAL_COPY(&temp, &result);

					// Delete compile results
					destroy_op_array(op_array);
					efree(op_array);
					if (!EG(exception)) {
						zval_ptr_dtor(&result);
					}
				}
			}
		}
	}


此时 `result` 变量就是我们案例中的 `$config` 变量，当然还可以使用 `zend_include_or_eval` 实现文件的包含，支持类型有：

- `ZEND_INCLUDE`
- `ZEND_INCLUDE_ONCE`
- `ZEND_REQUIRE`
- `ZEND_REQUIRE_ONCE`
