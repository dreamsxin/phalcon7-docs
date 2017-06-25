Class **Phalcon\\Cli\\Color**
=============================

.. role:: raw-html(raw)
   :format: html

:raw-html:`<a href="https://github.com/dreamsxin/cphalcon7/blob/master/ext/cli/color.c" class="btn btn-default btn-sm">Source on GitHub</a>`


.. code-block:: php

    <?php

    echo Phalcon\Cli\Color::head("head");
    echo Phalcon\Cli\Color::error("error");
    echo Phalcon\Cli\Color::success("success");
    echo Phalcon\Cli\Color::info("info");



Constants
---------

*integer* **FG_BLACK**

*integer* **FG_DARK_GRAY**

*integer* **FG_RED**

*integer* **FG_LIGHT_RED**

*integer* **FG_GREEN**

*integer* **FG_LIGHT_GREEN**

*integer* **FG_BROWN**

*integer* **FG_YELLOW**

*integer* **FG_BLUE**

*integer* **FG_LIGHT_BLUE**

*integer* **FG_PURPLE**

*integer* **FG_LIGHT_PURPLE**

*integer* **FG_CYAN**

*integer* **FG_LIGHT_CYAN**

*integer* **FG_LIGHT_GRAY**

*integer* **FG_WHITE**

*integer* **BG_BLACK**

*integer* **BG_RED**

*integer* **BG_GREEN**

*integer* **BG_YELLOW**

*integer* **BG_BLUE**

*integer* **BG_MAGENTA**

*integer* **BG_CYAN**

*integer* **BG_LIGHT_GRAY**

*integer* **AT_NORMAL**

*integer* **AT_BOLD**

*integer* **AT_ITALIC**

*integer* **AT_UNDERLINE**

*integer* **AT_BLINK**

*integer* **AT_OUTLINE**

*integer* **AT_REVERSE**

*integer* **AT_NONDISP**

*integer* **AT_STRIKE**

Methods
-------

public static *boolean*  **isSupportedShell** ()

Identify if console supports colors



public static *string*  **colorize** (*string* $str, [*null|integer* $fg], [*null|integer* $at], [*null|integer* $bg])

Colorizes the string using provided colors.



public static *string*  **head** (*string* $str)

Color style for head messages.



public static *string*  **error** (*string* $str)

Color style for error messages.



public static *string*  **success** (*string* $str)

Color style for success messages.



public static *string*  **info** (*string* $str)

Color style for info messages.



