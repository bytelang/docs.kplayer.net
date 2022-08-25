## 全局选项

这些全局选项在任何场景下均有效，它大部分影响整个程序的运行周期。可以设置比如初始化配置、日志级别等等

使用`--help`查看当前存在哪些可用的选项参数



## 查看帮助选项

在任意子命令下使用`--help`选项可以获得支持哪些子命令使用，也可以在子命令中执行`--help`获取子命令允许被支持哪些子命令与使用方法

```shell {12-18}
> ./kplayer --help
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
Usage:
  kplayer [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  help        Help about any command
  init        Init config file
  output      Output category
  play        Play category
  plugin      Plugin category
  resource    Resource category

Flags:
  -c, --config string      config file name (default "config")
  -h, --help               help for kplayer
      --home string        directory for config and data (default "./")
      --log_level string   The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
      --plain string       The logging format (json|plain) (default "plain")

Use "kplayer [command] --help" for more information about a command.
```





## 设置家目录

`homedir`在大多数软件设计中都存在相似的设计，它代表程序的根目录将会以哪个目录为主。因为在程序运行时会有不少读写的数据资源。例如配置文件、字体、缓存、插件等资源的读取，也有日志文件、下载的资源文件的写入。



::: tip 提醒

所以通常情况下`homedir`  必须具备完全的当前`Linux`的用户的读写权限

:::



默认情况下`homedir`的取值为当前运行的目录，你可以使用`--home`来指定任意的路径来改变它。如果使用了这个选项，所有的输出文件将会从当前运行的目录改变到指定的目录中。

正因为如此，所以你也需要保证在`/home/user/second-kplayer-directory`也需要存在`config.json`的配置文件

```shell
> ./kplayer play start --home /home/user/second-kplayer-directory
```



## 配置文件路径

默认的配置文件`config.json`在`homedir`目录下检索并解析，如果你存在多份不同的配置文件需要不同场景下切换使用。你可以显式指定配置文件的路径

```shell
> ./kplayer play start --config /home/user/second-config.json
```

在运行时，`KPlayer`将会从默认的`config.json`更在为`second-config.json`来解析。



::: tip 提醒

config与homedir并不冲突，改变config path仅仅只会更改配置文件的解析路径而对homedir不造成影响

:::



你可以使用更简单的选项参数来指定它

```shell
>./kplayer play start -c /home/user/second-config.json
```



## 配置日志格式

`KPlayer`允许对输出日志进行格式化输出，默认为`text/plain`格式文本格式输出。携带颜色、格式信息等。

你可以指定它输出为`json`的格式化日志，这方便对日志进行收集分析与健康检查的判断

```shell
> ./kplayer play start --plain json
```



## 配置日志级别

默认日志行为为`Info`级别的日志，不同场景下的打印日志便于过滤到一些调试、警告日志的产生。你可以显示指定它的级别来更好的获得程序当前运行的状态

```shell
> ./kplayer play start --log_level debug
```

