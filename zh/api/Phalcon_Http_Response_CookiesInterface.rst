Interface **Phalcon\\Http\\Response\\CookiesInterface**
=======================================================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/phalcon/http/response/cookiesinterface.zep" class="btn btn-default btn-sm">Source on GitHub</a>`

Phalcon\\Http\\Response\\CookiesInterface initializer


Methods
-------

abstract public :doc:`Phalcon\\Http\\Response\\CookiesInterface <Phalcon_Http_Response_CookiesInterface>`  **useEncryption** (*boolean* $useEncryption)

Set if cookies in the bag must be automatically encrypted/decrypted



abstract public *boolean*  **isUsingEncryption** ()

Returns if the bag is automatically encrypting/decrypting cookies



abstract public :doc:`Phalcon\\Http\\Response\\CookiesInterface <Phalcon_Http_Response_CookiesInterface>`  **set** (*string* $name, [*mixed* $value], [*int* $expire], [*string* $path], [*boolean* $secure], [*string* $domain], [*boolean* $httpOnly])

Sets a cookie to be sent at the end of the request



abstract public :doc:`Phalcon\\Http\\Cookie <Phalcon_Http_Cookie>`  **get** (*string* $name)

Gets a cookie from the bag



abstract public *boolean*  **has** (*string* $name)

Check if a cookie is defined in the bag or exists in the $_COOKIE superglobal



abstract public *boolean*  **delete** (*string* $name)

Deletes a cookie by its name This method does not removes cookies from the $_COOKIE superglobal



abstract public *boolean*  **send** ()

Sends the cookies to the client



abstract public :doc:`Phalcon\\Http\\Response\\CookiesInterface <Phalcon_Http_Response_CookiesInterface>`  **reset** ()

Reset set cookies



