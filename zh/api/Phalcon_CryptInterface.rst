Interface **Phalcon\\CryptInterface**
=====================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/cryptinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\CryptInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\CryptInterface <Phalcon_CryptInterface>`  **setMethod** (*unknown* $method)

Sets the cipher method



abstract public *string*  **getMethod** ()

Gets the cipher method



abstract public :doc:`Phalcon\\CryptInterface <Phalcon_CryptInterface>`  **setKey** (*string* $key)

Sets the encryption key



abstract public *string*  **getKey** ()

Returns the encryption key



abstract public *string*  **encrypt** (*string* $text, [*string* $key], [*unknown* $options])

Encrypts a text



abstract public *string*  **decrypt** (*string* $text, [*string* $key], [*unknown* $options])

Decrypts a text



abstract public *string*  **encryptBase64** (*string* $text, [*string* $key], [*unknown* $safe])

Encrypts a text returning the result as a base64 string



abstract public *string*  **decryptBase64** (*string* $text, [*string* $key], [*unknown* $safe])

Decrypt a text that is coded as a base64 string



abstract public *array*  **getAvailableMethods** ()

Returns a list of available methods



