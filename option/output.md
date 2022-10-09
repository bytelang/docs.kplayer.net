## 帮助选项

使用 `--help`查看`output`模块下提供的子命令列表

```shell {14-16}
> kplayer ./kplayer output --help
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
Kplayer output management commands. control kplayer output add,remove...

Usage:
  kplayer output [command]

Available Commands:
  add         add output resource.
  list        list output
  remove      remove output resource by unique name.

Flags:
  -h, --help   help for output

Global Flags:
  -c, --config string      config file name (default "config")
      --home string        directory for config and data (default "./")
      --log_level string   The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
      --plain string       The logging format (json|plain) (default "plain")

Use "kplayer output [command] --help" for more information about a command.
```



该模块的命令用于`KPlayer`已被成功运行，动态的通过命令行对输出资源进行修改操作



## 添加输出资源

`KPlayer`支持多地址推流，可以通过该命令在运行时动态添加输出流

| 参数        | 说明               | 是否可选 |
| ----------- | ------------------ | -------- |
| output_path | 想要添加的推流路径 | 否       |
| unique      | 资源的唯一ID       | 是       |



```shell
> ./kplayer output add "rtmp://127.0.0.1/live/new" "new"
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
output:
  path: rtmp://127.0.0.1:1935/live/new
  unique: new
```



## 查看输出列表

```shell
> ./kplayer output list
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
- connected: true
  create_time: 1661331653
  end_time: 0
  path: rtmp://127.0.0.1:1935/live/test
  start_time: 1661331653
  unique: 7rqu6f
- connected: true
  create_time: 1661331659
  end_time: 0
  path: rtmp://127.0.0.1:1935/live/new
  start_time: 1661331659
  unique: new
```



## 删除输出资源

```shell
> ./kplayer output remove new
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
output:
  path: rtmp://127.0.0.1:1935/live/new
  unique: new
```