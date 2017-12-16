Class **Phalcon\\Py\\Matplot**
==============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/py/matplot.c" class="btn btn-default btn-sm">Source on GitHub</a>`




Methods
-------

public static  **factory** ([*unknown* $backend])

...


private :doc:`Phalcon\\Py\\Matplot <Phalcon_Py_Matplot>`  **__construct** ([*unknown* $backend])

PHP_METHOD(Phalcon_Py_Matplot, factory) { zval *backend = NULL, instance = {}; phalcon_fetch_params(0, 0, 1, &backend); if (!backend) { backend = &PHALCON_GLOBAL(z_null); } phalcon_read_static_property_ce(&instance, phalcon_py_matplot_ce, SL("_instance"), PH_READONLY); if (Z_TYPE(instance) == IS_NULL) { object_init_ex(return_value, phalcon_py_matplot_ce); PHALCON_CALL_METHOD(NULL, return_value, "__construct", backend); phalcon_update_static_property_ce(phalcon_py_matplot_ce, SL("_instance"), return_value); } else { RETURN_CTOR(&instance); } } Phalcon\\Py\\Matplot constructor



public  **annotate** (*unknown* $annotation, *unknown* $x, *unknown* $y)

...


public  **plot** (*array* $x, [*array* $y], [*unknown* $format], [*unknown* $style], [*unknown* $label])

...


public  **fillBetween** (*array* $x, *array* $y1, *array* $y2, *array* $keywords)

...


public  **hist** (*array* $y, [*unknown* $bins], [*unknown* $color], [*unknown* $alpha], [*unknown* $label])

...


public  **errorbar** (*array* $x, *array* $y, *array* $yerr)

...


public  **figure** ()

...


public  **legend** ()

...


public  **ylim** (*unknown* $left, *unknown* $right)

...


public  **getYlim** ()

...


public  **xlim** (*unknown* $left, *unknown* $right)

...


public  **getXlim** ()

...


public  **subplot** ()

...


public  **title** (*unknown* $title)

...


public  **axis** (*unknown* $axis)

...


public  **xlabel** (*unknown* $xlabel)

...


public  **ylabel** (*unknown* $ylabel)

...


public  **grid** (*unknown* $flag)

...


public  **show** ()

...


public  **close** ()

...


public  **draw** ()

...


public  **pause** ()

...


public  **save** (*unknown* $filename)

...


public  **clf** ()

...


public  **tightLayout** ()

...


public *mixed*  **__call** (*string* $method, [*array* $arguments])

Handles method calls when a method is not implemented



