包含（require）
=============
在实际开发过程中，进程会在一个文件中包含另一个或者直接从另一个文件中返回一组数据;

实例 (instance)
--------------

.. code-block:: php

	$file = "/config.php";
	$config = require($file);

实现 (implementation)
---------------------

.. code-block:: c

	//check file exists
	if (VCWD_STAT(file_name, &file_sb) == 0) {
		//Whether it is a regular file
 		if (S_ISREG(file_sb.st_mode)) {
			//open file
       			if (( fh.handle.fp = VCWD_FOPEN(file_name, "r") )) {
          			fh.filename = file_name;
             			fh.type = ZEND_HANDLE_FILENAME;
             			fh.free_filename = 0;
             			fh.opened_path = NULL;

				//compile file
             			op_array = zend_compile_file(&fh, ZEND_REQUIRE TSRMLS_CC);

				//delete file handle
                                zend_destroy_file_handle(&fh);

				//check compile results
                                if (op_array) {
                                    zval result;
                                    ZVAL_UNDEF(&result);
				    
				    //access to compile the results
                                    zend_execute(op_array, &result);
				    //result => $config

                                    ZVAL_COPY(&temp, &result);

				    //delete compile results
                                    destroy_op_array(op_array);
                                    efree(op_array);
                                    if (!EG(exception)) {
                                        zval_ptr_dtor(&result);
                                    }
                                }
                            }
                        }
                    }


此时result变量就是我们案例中的$config变量；当然还有以下宏可用，和php中一样；

.. code-block:: c

	ZEND_INCLUDE、ZEND_INCLUDE_ONCE、ZEND_REQUIRE、ZEND_REQUIRE_ONCE
