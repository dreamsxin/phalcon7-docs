Interface **Phalcon\\Http\\Request\\FileInterface**
===================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/http/request/fileinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Http\\Request\\FileInterface initializer


Methods
-------

abstract public *int*  **getSize** ()

Returns the file size of the uploaded file



abstract public *string*  **getName** ()

Returns the real name of the uploaded file



abstract public *string*  **getTempName** ()

Returns the temporal name of the uploaded file



abstract public *string*  **getType** ()

Returns the mime type reported by the browser This mime type is not completely secure, use getRealType() instead



abstract public *string*  **getRealType** ()

Gets the real mime type of the upload file using finfo



abstract public *boolean*  **moveTo** (*string* $destination)

Move the temporary file to a destination



