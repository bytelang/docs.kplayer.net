## 配置文件简介

`KPlayer`的用户自定义参数通过`json`格式的层级来确定自定义参数。

由于`json`规范为严格模式，所以在配置文件中请勿掺杂`Javascript`语法的注释和非严格的`,`结束分隔符。



## 自定义路径

在默认情况下，优先查找程序运行的当前目录下的`config.json`文件 。

你可以通过显式指定`homedir`或者配置文件的完整路径来改变它的默认值。详情使用方法[访问这里](#)