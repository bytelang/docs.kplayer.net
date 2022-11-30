## 帮助选项

使用 `--help`查看`play`模块下提供的子命令列表

```shell {14-21}
> kplayer ./kplayer play --help
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
App management commands. control kplayer basic status

Usage:
  kplayer play [command]

Available Commands:
  continue    continue player
  duration    get player duration status
  info        get Information play
  pause       pause player
  skip        skip play current resource
  start       Start kplayer
  status      Print kplayer status
  stop        Start kplayer

Flags:
  -h, --help   help for play

Global Flags:
  -c, --config string      config file name (default "config")
      --home string        directory for config and data (default "./")
      --log_level string   The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
      --plain string       The logging format (json|plain) (default "plain")

Use "kplayer play [command] --help" for more information about a command.
```



该模块的命令用于`KPlayer`已被成功运行，动态的通过命令行对播放器进行控制操作



## 继续播放

类似播放器中暂停/继续功能，此处控制在暂停状态继续播放

```shell
> ./kplayer play continue
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
{}
```



## 当前运行时间

获取`KPlayer` 本次运行从合适开始已运行了多久时间

```shell
> ./kplayer play duration
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
duration_timestamp: 7
start_timestamp: 1661329296
```



## 获取基础信息

获取`KPlayer`的基础信息

```shell
> ./kplayer play info
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
libkplayer_version: v1.4.14
license_version: v1
major_version: v0.5.6
plugin_version: 1.5.1
start_time: 2022-08-10 09:17:46.578142281 +0800 CST m=+0.470338950
start_time_timestamp: 1660094266
```



| 返回值               | 说明                   |
| -------------------- | ---------------------- |
| libkplayer_version   | libkplayer使用的版本号 |
| license_version      | 授权协议版本号         |
| major_version        | 主版本号               |
| plugin_version       | 插件适配版本号         |
| start_time           | 开始运行格式化时间     |
| start_time_timestamp | 开始运行时间戳         |



## 播放暂停

```shell
> ./kplayer play pause
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
{}
```



## 跳过当前播放资源

```shell
> ./kplayer play skip
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
{}
```



## 开始运行

开始运行当前程序开始进行编解码

```shell
> ./kplayer play start
```



作为主程序开始的入口，它单独存在两个运行参数提供在后台运行与仅构建缓存模式

同时它支持两个参数选项
1. `-g`或者`--generate_cache` 使用该参数会忽略推流输出列表，仅仅参与缓存文件的构建。
它生成缓存的速度比正常播放一边要花费的时间更短，具体时间取决于你的服务器性能
```shell
./kplayer play start -g
```

2. `-d`或者`--daemon` 使用该参数会使得`KPlayer`运行时放在后台，由Linux系统的守护进程来确保`ssh`结束后程序不会立马退出
```shell
./kplayer play start -d 
```



## 获取运行状态

获取当前程序是否正常运行，通过获取记录的`pid`是否仍然在进程列表中。

这个功能也可以用来查看在[后台运行](#)的情况下，是否仍然程序处在运行状态中。

```shell
> ./kplayer play status
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
INFO[2022-08-24 16:30:41] kplayer active running on daemon mode         pid=3560168 status=on
```



## 结束运行

结束当前运行实例。

这个功能也可以用来查看在[后台运行](#)的情况下，结束后台运行进程。

```shell
> ./kplayer play stop
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
INFO[2022-08-24 16:33:04] kplayer stop success
```

