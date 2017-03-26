Throwing Exceptions
===================
When you throw an exception using the Phalcon API, the current flow of execution will be stopped, returning
to the last PHP code block when a Phalcon method where called.

There are two ways to throw exceptions, the first, when the exception object only receives a string as parameter:

.. code-block:: c

	PHALCON_THROW_EXCEPTION_STR(phalcon_exception_ce, "Hey this is an exception");

Or building the exception manually and then throwing it:

.. code-block:: c

	PHALCON_CONCAT_SVS(&exception_message, "Unable to insert into ", table, " without data");

	object_init_ex(&exception, phalcon_db_exception_ce);

	// The exception constructor must be manually called
	PHALCON_CALL_METHOD(NULL, &exception, "__construct", &exception_message);
	phalcon_throw_exception(&exception);
	return;
