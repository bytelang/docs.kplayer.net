## 帮助选项

使用 `--help`查看`resource`模块下提供的子命令列表

```shell {14-19}
> kplayer ./kplayer resource --help
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
Kplayer resource management commands. control kplayer resource add,remove...

Usage:
  kplayer resource [command]

Available Commands:
  add         add resource to playlist
  all         gets the list of resources
  current     get the list of current play resource
  list        gets the list of unplayed resources
  remove      remove resource to playlist by unique name
  seek        seeks in current resource to seconds position

Flags:
  -h, --help   help for resource

Global Flags:
  -c, --config string      config file name (default "config")
      --home string        directory for config and data (default "./")
      --log_level string   The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
      --plain string       The logging format (json|plain) (default "plain")

Use "kplayer resource [command] --help" for more information about a command.
```



该模块的命令用于`KPlayer`已被成功运行，动态的通过命令行对资源进行修改操作



## 添加推流资源

| 参数       | 说明               | 是否可选 |
| ---------- | ------------------ | -------- |
| input_path | 想要添加的资源路径 | 否       |
| unique     | 资源的唯一ID       | 是       |



```shell
> ./kplayer resource add "/home/user/video/起风了.flv" "qfl"
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
resource:
  create_time: 0
  end_time: 0
  path: /home/user/video/起风了.flv
  start_time: 0
  unique: qfl
```



## 查看资源列表

```shell
> ./kplayer resource all
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
resource:
- create_time: 1661327615
  end_time: 0
  path: /Users/kangkai/smart/video/起风了.flv
  start_time: 0
  unique: qfl
```



## 查看当前播放资源

```shell
> ./kplayer resource current
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
duration: 325
duration_format: "0:5:25"
hit_cache: false
resource:
  create_time: 1661327588
  end_time: 0
  path: /Users/kangkai/smart/video/起风了.flv
  start_time: 1661327588
  unique: mMRzUj
seek: 289
seek_format: "0:4:49"
```



| 返回值          | 说明                |
| --------------- | ------------------- |
| duration        | 视频资源总长度(秒） |
| duration_foramt | 格式化时分秒总长度  |
| resource        | 资源基础属性        |
| seek            | 当前播放时间(秒）   |
| seek_format     | 格式化当前播放时间  |



## 查看未播放资源列表

```shell
> ./kplayer resource list
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
resource:
- create_time: 1661327615
  end_time: 0
  path: /Users/kangkai/smart/video/起风了.flv
  start_time: 0
  unique: qfl
```



## 删除指定资源

无法删除正在播放的资源。删除指定`unique`name 的资源对象

```shell
> ./kplayer resource remove qfl
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
resource:
  create_time: 1661328455
  path: /Users/kangkai/smart/video/起风了.flv
  unique: qfl
```



## 跳转至指定资源

跳转至指定资源与指定时间

| 参数   | 说明                                                         | 是否可选 |
| ------ | ------------------------------------------------------------ | -------- |
| unique | 资源unique id。允许传入空字符串，若为空字符串则默认为当前播放资源 | 否       |
| seek   | 跳转的秒数                                                   | 否       |



```shell
> ./kplayer resource seek "" 10
kplayer for golang v0.5.6 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.4.14 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.21.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
resource:
  create_time: 1661328455
  path: /Users/kangkai/smart/video/起风了.flv
  seek: 10
  start_time: 1661328854
  unique: qfl
```

