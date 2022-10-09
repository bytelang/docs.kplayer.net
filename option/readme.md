## 简介

`KPlayer`可执行文件提供子模块方式的交互式命令行。它可以提供运行前定义参数设置、运行期间的动态控制。



可以使用`--help`来插件根命令与子命令的使用方法，例如

```shell
> ./kplayer --help
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
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





## 目录列表

下方列举了`KPlayer`在运行时会涉及到目录列表

```shell
./kplayer
├── cache
├── log
├── plugin
└── resource

4 directories, 0 files
```



1. cache目录保存开启缓存功能时输出的缓存文件目录

   

2. log保存程序运行时产生的日志文件与pid文件。其中core.log为`libkplayer`输出的日志文件

   

3. plugin保存需要加载或自动下载的插件后缀名为`kpe`插件文件

   

4. resource包含运行期间依赖的资源文件，例如字体等



## 使用条件

全局配置仅仅作为运行期间的自定义参数配置，无使用限制。但在使用各自模块中的子命令操作时需要保证`KPlayer`的`rpc`功能已被开启，因为cli的控制行为本质上是调用`rpc`接口来完成命令的发送与接收