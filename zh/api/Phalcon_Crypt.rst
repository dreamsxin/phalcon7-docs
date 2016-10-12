Class **Phalcon\\Crypt**
========================

*implements* :doc:`Phalcon\\CryptInterface <Phalcon_CryptInterface>`

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/crypt.c" class="btn btn-default btn-sm">Source on GitHub</a>`

Provides encryption facilities to phalcon applications  

.. code-block:: php

    <?php

    $crypt = new Phalcon\Crypt();
    
    $key = 'le password';
    $text = 'This is a secret text';
    
    $encrypted = $crypt->encrypt($text, $key);
    
    echo $crypt->decrypt($encrypted, $key);



Methods
-------

public *Phalcon\\Encrypt*  **setMethod** (*string* $method)

Sets the cipher method



public *string*  **getMethod** ()

Returns the current cipher method



public *Phalcon\\Encrypt*  **setKey** (*string* $key)

Sets the encryption key



public *string*  **getKey** ()

Returns the encryption key



public *string*  **encrypt** (*string* $text, [*string* $key], [*unknown* $options])

Encrypts a text 

.. code-block:: php

    <?php

    $encrypted = $crypt->encrypt("Ultra-secret text", "encrypt password");




public *string*  **decrypt** (*string* $text, [*string* $key], [*unknown* $options])

Decrypts an encrypted text 

.. code-block:: php

    <?php

    echo $crypt->decrypt($encrypted, "decrypt password");




public *string*  **encryptBase64** (*string* $text, [*string* $key], [*unknown* $safe])

Encrypts a text returning the result as a base64 string



public *string*  **decryptBase64** (*string* $text, [*string* $key], [*unknown* $safe])

Decrypt a text that is coded as a base64 string



public *array*  **getAvailableMethods** ()

Returns a list of available modes



public  **beforeEncrypt** (*callable* $handler)

Adds a internal hooks before encrypts a text



public  **afterEncrypt** (*callable* $handler)

Adds a internal hooks after encrypts a text



public  **beforeDecrypt** (*callable* $handler)

Adds a internal hooks before decrypts an encrypted text



public  **afterDecrypt** (*callable* $handler)

Adds a internal hooks after decrypts an encrypted text



