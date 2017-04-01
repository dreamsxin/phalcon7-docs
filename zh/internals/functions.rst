调用函数（Calling Functions）
=============================
Calling functions is another common action we do when create programs in PHP. Although many functions may be called directly using its internal function pointer in C, others can simply being called using the PHP userland. For example:

.. code-block:: c

	// $length = strlen(some_variable);
	PHALCON_CALL_FUNCTION(&length, "strlen", &some_variable);

	// Calling substr() with its 3 arguments returning the substring into "part"
	PHALCON_CALL_FUNCTION(&part, "substr", &some_variable, &start, &length);

	// Calling ob_start(), this function does not return anything
	PHALCON_CALL_FUNCTION(NULL, "ob_start");

	// Closing a file with fclose
	PHALCON_CALL_FUNCTION(NULL, "fclose", file_handler);

如上所述，PHP 已经有帮我们做了很多事情，C 的扩展并不意味着我们要重新发明轮子。我们也要尽量避免使用 C 非常底层的特性。使用 PHP 函数帮助我们实现和 PHP 编程中类似的行为，这样我们就可以避免可能出现的错误。

在Phalcon中，`PHALCON_CALL_FUNCTION`调用的是Phalcon为我们封装的`phalcon_call_method_with_params`函数，利用该函数可以很轻松的调用内核及自定义函数，其函数调用了Zend API。
  
 .. code-block:: c

 	#define call_user_function_ex(function_table, object, function_name, retval_ptr, param_count, params, no_separation, symbol_table) \
 	_call_user_function_ex(object, function_name, retval_ptr, param_count, params, no_separation)
 
 
 除了`call_user_function_ex`以及`call_user_function`,还有`zend_call_method`;

----------

The following code opens a file in C and write something on it. Its functionality is limited because it only works on
local files:

.. code-block:: c

	FILE * pFile;
	pFile = fopen ("myfile.txt","w");
	if (pFile != NULL) {
		fputs ("fopen example",pFile);
		fclose (pFile);
	}

Now write the same code using the PHP userland:

.. code-block:: c

	ZVAL_STRING(&mode, "w");

	PHALCON_CALL_FUNCTION(&file_handler, "fopen", &file_path, &mode);

	if (PHALCON_IS_NOT_FALSE(&file_handler)) {
		ZVAL_STRING(&text, "fopen example");

		PHALCON_CALL_FUNCTION(NULL, "fputs", &file_handler, &text);

		PHALCON_CALL_FUNCTION(NULL, "fclose", &file_handler);
	}

Although both codes perform the same task, the former is more powerful as it could open a PHP stream, a file in a URL
 or a local file. We can also write the same code using the PHP API, without losing functionality. However, the
 above code is more familiar if we are primarily PHP developers.

The same code in PHP:

.. code-block:: php

	<?php

	$fp = fopen($file_path, "w");
	if($fp){
		fputs($fp, "fopen example");
		fclose($fp);
	}
