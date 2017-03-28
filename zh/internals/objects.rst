操作对象（Objects Manipulation）
================================
Phalcon is a pure object-oriented framework for PHP. In this chapter, we explain how to make most common operations
on objects using the Phalcon API.

创建与实例化（Creation/Instantiation）
--------------------------------------
Instantiate objects of the framework classes is easy:

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
