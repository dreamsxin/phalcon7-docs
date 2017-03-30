类（Classes）
=============
Phalcon7 框架主要是由类组成，而类由命名空间统一组织。本文档将教你如何实现一个类及其方法。

注册类（Registering Classes）
-----------------------------
在 ext 目录增加 auth.h 文件，注册 Phalcon\\Auth 类：

.. code-block:: c

	#ifndef PHALCON_AUTH_H
	#define PHALCON_AUTH_H

	#include "php_phalcon.h"

	extern zend_class_entry *phalcon_auth_ce;

	PHALCON_INIT_CLASS(Phalcon_Auth);

	#endif /* PHALCON_AUTH_H */

注册方法和它的参数（Registering methods and its arguments）
-----------------------------------------------------------
然后，我们创建 auth.c 文件，在里面添加方法的原型：

.. code-block:: c

	PHP_METHOD(Phalcon_Auth, __construct);
	PHP_METHOD(Phalcon_Auth, getIdentity);
	PHP_METHOD(Phalcon_Auth, auth);

之后我们为每个方法添加参数信息，在这里我们为类的构造方法添加参数信息：

.. code-block:: c

	ZEND_BEGIN_ARG_INFO_EX(arginfo_phalcon_auth__construct, 0, 0, 2)
		ZEND_ARG_INFO(0, adapter)
		ZEND_ARG_ARRAY_INFO(0, options, 0)
	ZEND_END_ARG_INFO()

现在，我们将所有方法赋予指定的类：

.. code-block:: c

	static const zend_function_entry phalcon_auth_method_entry[] = {
		PHP_ME(Phalcon_Auth, __construct, arginfo_phalcon_auth__construct, ZEND_ACC_PUBLIC)
		PHP_ME(Phalcon_Auth, getIdentity, NULL, ZEND_ACC_PUBLIC)
		PHP_ME(Phalcon_Auth, auth, NULL, ZEND_ACC_PUBLIC)
		PHP_FE_END
	};

定义方法（Implementing a method）
---------------------------------
仍然在 auth.c 文件中，我们添加代码：

.. code-block:: c

	// PHP_METHOD(class_name, method_name)
	PHP_METHOD(Phalcon_Auth, __construct){

		zval *adapter_name, *options = NULL;

		// Receive the method parameters
		if (zend_parse_parameters(ZEND_NUM_ARGS(), "zz", &adapter_name, &options) == FAILURE) {
			RETURN_NULL();
		}
	}

With the above code we create the constructor of the class Phalcon\\Auth, a method is defined with the macro
PHP_METHOD, first we put the class name and then the name of the method, although Phalcon uses namespaces,
class names have _ instead of \\:

.. code-block:: c

	PHP_METHOD(Phalcon_Auth, __construct){

If the method has parameters we receive them using zend_parse_parameters:

.. code-block:: c

	if (zend_parse_parameters(ZEND_NUM_ARGS(), "zz", &adapter_name, &options) == FAILURE) {
		RETURN_NULL();
	}

If we do not receive the correct number of parameters will result in an error message. You see, there's an argument
"zz" to receive the parameters, this indicates the type of data received and the number of them. In the above example
that means that the method is receiving two parameters. If they were three zval then it should be "zzz".

Then the variables are received in respective order: &adapter_name, &options
