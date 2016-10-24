# Phalcon7 Framework Documentation

我们的使命是给开发者提供一个简单但不简陋的 web 开发工具。

## 生成 HTML 文档

```shell
sudo apt-get install sphinx-common
# or
sudo apt install python-pip
git clone https://github.com/dreamsxin/sphinx.git
cd sphinx
pip install . -i http://pypi.douban.com/simple --trusted-host pypi.douban.com

cd zh
make html
```

## API 文档生成

通过以下命令将自动从Phalcon项目C文件读取注释并生成相应 API 文档:

    php scripts/gen-api.php

如果您找到任何错误或者想帮助改进可以 fork 项目，提交合并请求。

项目地址：
- https://github.com/dreamsxin/phalcon7-docs (documentation)
- https://github.com/dreamsxin/cphalcon7 (source code)
- https://github.com/dreamsxin/cphalcon (source code)
