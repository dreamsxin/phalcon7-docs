Class **Phalcon\\Arr**
======================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/arr.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Provides utilities to work with arrs


Methods
-------

public static *boolean*  **is_assoc** (*array* $array)

Tests if an array is associative or not. // Returns TRUE \\Phalcon\\Arr::is_assoc(array('username' => 'john.doe'))



public static *boolean*  **is_array** (*unknown* $array)

Test if a value is an array with an additional check for array-like objects. // Returns TRUE \\Phalcon\\Arr::is_array(array());



public static *mixed*  **path** (*array* $array, *mixed* $path, [*unknown* $default_value], [*string* $delimiter])

Gets a value from an array using a dot separated path. // Get the value of $array['foo']['bar'] $value = \\Phalcon\\Arr::path($array, 'foo.bar'); Using a wildcard "*" will search intermediate arrays and return an array. // Get the values of "color" in theme $colors = \\Phalcon\\Arr::path($array, 'theme.*.color'); // Using an array of keys $colors = \\Phalcon\\Arr::path($array, array('theme', '*', 'color'));



public static  **set_path** (*array* $array, *string* $path, *mixed* $value, [*string* $delimiter], [*unknown* $flag])

Set a value on an array by path. Using a wildcard "*" will search intermediate arrays and return an array. // Set the values of "color" in theme $array = array('theme' => array('one' => array('color' => 'green'), 'two' => array('size' => 11)); \\Phalcon\\Arr::set_path($array, 'theme.*.color', 'red'); // Result: array('theme' => array('one' => array('color' => 'red'), 'two' => array('size' => 11, 'color' => 'red'));



public static *array*  **range** ([*integer* $step], [*integer* $max])

Fill an array with a range of numbers. // Fill an array with values 5, 10, 15, 20 $values = \\Phalcon\\Arr::range(5, 20);



public static *mixed*  **get** (*array* $array, *string|array|\Closure* $key, [*mixed* $default_value])

Retrieve a single key from an array. If the key does not exist in the array, the default value will be returned instead. // Get the value "username" from $_POST, if it exists $username = \\Phalcon\\Arr::get($_POST, 'username');



public static *mixed*  **first** (*array* $array, *string|array|\Closure* $key, [*mixed* $default_value])

Retrieve a single key from an array, if value an array return the first element.



public static *mixed*  **choice** (*array* $array, *string* $key, *string* $value1, [*string* $value2])

Choice one value, If the key does not exist in the array, the value2 will be returned instead. // Choice the "value1", if exists the value "email" of $_POST $username = \\Phalcon\\Arr::choice($_POST, 'email', 'value1', 'value2');



public static *array*  **extract** (*array* $array, *array* $paths, [*mixed* $default_value])

Retrieves multiple paths from an array. If the path does not exist in the array, the default value will be added instead. // Get the values "username", "password" from $_POST $auth = \\Phalcon\\Arr::extract($_POST, array('username', 'password')); // Get the value "level1.level2a" from $data $data = array('level1' => array('level2a' => 'value 1', 'level2b' => 'value 2')); \\Phalcon\\Arr::extract($data, array('level1.level2a', 'password'));



public static *array*  **pluck** (*array* $array, *string* $key)

Retrieves muliple single-key values from a list of arrays. // Get all of the "id" values from a result $ids = \\Phalcon\\Arr::pluck($result, 'id');



public static *array*  **unshift** (*array* $array, *string* $key, *mixed* $val)

Adds a value to the beginning of an associative array. // Add an empty value to the start of a select list \\Phalcon\\Arr::unshift($array, 'none', 'Select a value');



public static *array*  **map** (*mixed* $callbacks, *array* $array, [*array* $keys])

Recursive version of [array_map](http://php.net/array_map), applies one or more callbacks to all elements in an array, including sub-arrays. // Apply "strip_tags" to every element in the array $array = \\Phalcon\\Arr::map('strip_tags', $array); // Apply $this->filter to every element in the array $array = \\Phalcon\\Arr::map(array(array($this,'filter')), $array);



public static *array*  **merge** (*array* $array1, *unknown* $array2)

Recursively merge two or more arrays. Values in an associative array overwrite previous values with the same key. Values in an indexed array are appended, but only when they do not already exist in the result. Note that this does not work the same as [array_merge_recursive](http://php.net/array_merge_recursive)! $john = array('name' => 'john', 'children' => array('fred', 'paul', 'sally', 'jane')); $mary = array('name' => 'mary', 'children' => array('jane')); // John and Mary are married, merge them together $john = \\Phalcon\\Arr::merge($john, $mary); // The output of $john will now be: array('name' => 'mary', 'children' => array('fred', 'paul', 'sally', 'jane'))



public static *array*  **overwrite** (*array* $array1, *array* $array2)

Overwrites an array with values from input arrays. Keys that do not exist in the first array will not be added! $a1 = array('name' => 'john', 'mood' => 'happy', 'food' => 'bacon'); $a2 = array('name' => 'jack', 'food' => 'tacos', 'drink' => 'beer'); // Overwrite the values of $a1 with $a2 $array = \\Phalcon\\Arr::overwrite($a1, $a2); // The output of $array will now be: array('name' => 'jack', 'mood' => 'happy', 'food' => 'tacos')



public static *array function, params*  **callback** (*string* $str)

Creates a callable function and parameter list from a string representation. Note that this function does not validate the callback string. // Get the callback function and parameters list($func, $params) = \\Phalcon\\Arr::callback('Foo::bar(apple,orange)'); // Get the result of the callback $result = call_user_func_array($func, $params);



public static *array*  **flatten** (*array* $array)

Convert a multi-dimensional array into a single-dimensional array. $array = array('set' => array('one' => 'something'), 'two' => 'other'); // Flatten the array $array = \\Phalcon\\Arr::flatten($array); // The array will now be array('one' => 'something', 'two' => 'other');



public static *ArrayObject*  **arrayobject** (*array* $array)

Convert a array to a array object. $array = array('name' => 'Phalcon7', 'version' => '1.0.x'); $arrayobject = \\Phalcon\\Arr::arrayobject($array);



public static *mixed*  **key** (*array* $array, [*int* $postion])

Gets array key of the postion $array = array('name' => 'Phalcon7', 'version' => '1.0.x'); $key = \\Phalcon\\Arr::key($array, 1);



public static *array*  **filter** (*array* $array, [*unknown* $callback])

Filters elements of an array using a the filter $array = array('name' => 'Phalcon7', 'version' => '1.0.x'); $key = \\Phalcon\\Arr::filter($array, 'int');



public static *mixed*  **sum** (*array* $array, [*mixed* $path])

Return the sum of all the values in the array using a dot separated path



public static *array*  **toArray** (*object|array|string* $object, [*array* $properties], [*bool* $recursive], [*unknown* $negate])

Converts an object or an array of objects into an array 

.. code-block:: php

    <?php

    print_r(Phalcon\Arr::toArray($user);




