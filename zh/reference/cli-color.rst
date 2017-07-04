命令行设置文字颜色（Command Line Text Color）
=============================================
允许在 xterm、ddterm、linux 等终端下生成带颜色的信息。

.. code-block:: php

    <?php

    use Phalcon\Cli\Color;

    if (Color::isSupportedShell()) {
	   echo 'Supported color'.PHP_EOL;
	}

    echo Color::colorize("hello", Color::FG_BLACK, Color::AT_BOLD, Color::BG_BLUE).PHP_EOL;
    echo Color::head("hello");
    echo Color::error("hello");
    echo Color::success("hello");
    echo Color::info("hello");
