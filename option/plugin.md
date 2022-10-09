## 帮助选项

使用 `--help`查看`plugin`模块下提供的子命令列表

```shell {14-17}
> kplayer ./kplayer plugin --help
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
Kplayer plugin management commands. control kplayer plugin add,remove...

Usage:
  kplayer plugin [command]

Available Commands:
  add         add plugin
  list        list plugin
  remove      remove plugin
  update      update plugin

Flags:
  -h, --help   help for plugin

Global Flags:
  -c, --config string      config file name (default "config")
      --home string        directory for config and data (default "./")
      --log_level string   The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
      --plain string       The logging format (json|plain) (default "plain")

Use "kplayer plugin [command] --help" for more information about a command.
```



该模块的命令用于`KPlayer`已被成功运行，动态的通过命令行对输插件资源进行修改操作



## 添加插件

通过该命令在运行时动态添加插件。

参数需要通过数组形式的方式传入，通过`--param`形式传入

| 参数   | 说明               | 是否可选 |
| ------ | ------------------ | -------- |
| name   | 想要添加的插件名称 | 否       |
| unique | 资源的唯一ID       | 是       |



```shell
> ./kplayer plugin add show-text mytext --param "fontsize=20" --param "text=hello kplayer"
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
plugin:
  create_time: 1661332101
  loaded_time: 1661332101
  params:
    fontsize: "20"
    text: hello kplayer
  path: plugin/show-text.kpe
  unique: mytext
```



## 查看插件列表

```shell
> ./kplayer plugin list
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
plugins:
- create_time: 1661332101
  loaded_time: 1661332101
  params:
    fontsize: "20"
    text: hello kplayer
  path: plugin/show-text.kpe
  unique: mytext
```



## 更新插件参数

如果想要动态更新插件参数，推荐使用`update`方法。它的更新效率要比删除插件再重新添加要高得多

```shell
> ./kplayer plugin update mytext --param "text=update text"
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
plugin:
  create_time: 1661332101
  loaded_time: 1661332101
  params:
    fontcolor: white
    fontfile: resource/font.ttf
    fontsize: "20"
    text: update text
    x: "0"
    y: "0"
  path: plugin/show-text.kpe
  unique: mytext
```



## 删除插件

```shell
> ./kplayer plugin remove mytext
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
plugin:
  create_time: 1661332101
  loaded_time: 1661332101
  params:
    fontcolor: white
    fontfile: resource/font.ttf
    fontsize: "20"
    text: update text
    x: "0"
    y: "0"
  path: plugin/show-text.kpe
  unique: mytext
```

