操作对象（Objects Manipulation）
================================
针对对象属性的操作，Phalcon API 在 Zend API 基础上封装了更多的函数（kernel/object.h），通过传递标志位（flag）自动完引用计数的处理。

标志位（flag）
^^^^^^^^^^^^^^

+----------------+--------------------+
| 标志位值       | 描述               |
+================+====================+
| PH_NOISY       | 值不存在时发出警告 |
+----------------+--------------------+
| PH_READONLY    | 不增加引用计数     |
+----------------+--------------------+
| PH_COPY        | 增加引用计数       |
+----------------+--------------------+

常用函数列表
^^^^^^^^^^^^

+----------------------------+
| 函数名                     |
+============================+
| phalcon_isset_property     |
+----------------------------+
| phalcon_read_property      |
+----------------------------+
| phalcon_update_property    |
+----------------------------+

创建与实例化（Creation/Instantiation）
--------------------------------------
实例化框架中的类很容易：

.. code-block:: c

	// Instantiate a object from the Phalcon\Mvc\Router\Route class entry
	object_init_ex(&route, phalcon_mvc_router_route_ce);

	// Calling the constructor and passing a pattern as parameter
	ZVAL_STRING(&pattern, "#^/([a-zA-Z0-9\\_]+)[/]{0,1}$#", 1);

	PHALCON_CALL_METHOD(&route, "__construct", &pattern);

The above code is the same as doing in PHP:

.. code-block:: php

	<?php

	$route = new Phalcon\Mvc\Router\Route("#^/([a-zA-Z0-9\\_]+)[/]{0,1}$#");

Moreover, if is not a Phalcon class then objects must then initialized as follows:

.. code-block:: c

	zend_class_entry *reflection_ce;

	// Obtain the ReflectionClass class entry, this will also call autoloaders
	reflection_ce = zend_fetch_class(SL("ReflectionClass"), ZEND_FETCH_CLASS_AUTO TSRMLS_CC);

	// Instantiate the Reflection object
	object_init_ex(&reflection, reflection_ce);

	// Pass a class name as constructor's parameter
	PHALCON_CALL_METHOD(NULL, reflection, "__construct", &class_name);

读写属性（Reading/Writing Properties）
--------------------------------------
Writing scalar values:

.. code-block:: c

	// Create a stdClass object
	object_init(&employee);

	// $employee->name = "Sonny"
	phalcon_update_property_string(&employee, SL("name"), "Sonny");

	// $employee->age = 23
	phalcon_update_property_long(&employee, SL("age"), 23);

	// Read the "name" property $name = $employee->name
	phalcon_read_property(&name, &employee, SL("name"), PH_NOISY_CC);

Assigning other zvals to properties:

.. code-block:: c

	ZVAL_STRING(&language, "English");

	object_init(&employee);

	// $employee->language = $language
	phalcon_update_property_zval(&employee, SL("language"), &language);

Reading/Writing dynamical properties:

.. code-block:: c

	ZVAL_STRING(&language, "English");

	ZVAL_STRING(&property, "language");

	object_init(&employee);

	// $employee->$property = $language
	phalcon_update_property_zval_zval(&employee, &property, &language);

	// $user_language = $employee->$property
	phalcon_read_property_zval(&user_language, &employee, &property, PH_NOISY_CC);


Reading/Writing static properties:

.. code-block:: c

	// Updating a static member with a string zval
	ZVAL_STRING(&greeting, "hello world");
	phalcon_update_static_property(SL("phalcon\\some\\component"), SL("_someString"), &greeting);

	// Updating a static member with a long zval
	PHALCON_INIT_VAR(number);
	ZVAL_LONG(number, 150);
	phalcon_update_static_property(SL("phalcon\\some\\component"), SL("_someInteger"), &number);

	// Reading a static member
	phalcon_read_static_property(&number, SL("phalcon\\some\\component"), SL("_someInteger"));
