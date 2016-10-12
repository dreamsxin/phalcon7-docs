Interface **Phalcon\\Http\\Response\\HeadersInterface**
=======================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/http/response/headersinterface.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Http\\Response\\HeadersInterface initializer


Methods
-------

abstract public  **set** (*string* $name, *string* $value)

Sets a header to be sent at the end of the request



abstract public *string*  **get** (*string* $name)

Gets a header value from the internal bag



abstract public  **setRaw** (*string* $header)

Sets a raw header to be sent at the end of the request



abstract public *boolean*  **send** ()

Sends the headers to the client



abstract public  **reset** ()

Reset set headers



abstract public *array*  **toArray** ()

Returns the current headers as an array



