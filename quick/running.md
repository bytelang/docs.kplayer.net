## 开始运行KPlayer

进行到这里，符合条件的配置文件与环境在上一步已经配置完成，执行下方的命令即可开始`KPlayer` 进行视频资源推流。

::: tip 提醒

如果你推流的线上推流服务器。请保证您的直播间或者推流服务器是开启状态。某些平台在一段时间后未接收推流资源将会自动关闭，你可以关闭再重新打开

:::



执行开始推流的命令

``` shell
./kplayer play start
```

将会看到以下输出信息并保持程序继续运行，即成功推流

```shell
kplayer for golang v0.5.7 Copyright(c) 2019-2022 the ByteLang Studio (https://kplayer.bytelang.cn)
  libkplayer version: v1.5.2 plugin version: 1.5.1 license version: v1
  toolchains GNU(10.3.1) C++ Standard 17 on Linux-x86_64-5.18.14-arch1-1
  build with build-chains cmake(3.22.3) type with Release
  Hope you have a good experience.
-------------------------------------------------------------------------------------------------------------------
INFO[2022-08-23 15:25:05] grpc server listening                         address=127.0.0.1 port=5157
INFO[2022-08-23 15:25:05] http server listening                         address=127.0.0.1 port=5156
INFO[2022-08-23 15:25:05] output add success                            path="rmtp://127.0.0.1:1935/live/test" unique=33f043
INFO[2022-08-23 15:25:05] core start up success
INFO[2022-08-23 15:25:05] kplayer start success
INFO[2022-08-23 15:25:05] checked play resource                         duration=325 path="/home/user/video/起风了.flv" unique=mMRzUj
```



## 查看推流内容

如果是在线直播平台，打开你的直播间链接可以看到视频资源正确在播放

如果是自己搭建的推流服务端，通过可以播放rtmp协议的播放器例如`ffplay`或`vlc`打开推流链接可以查看到资源播放情况



## 如何在后台执行

默认情况下通过`ssh`进入到服务器中，当前程序的父进程为ssh-agent。当退出终端时，程序将会被结束

你可以通过`nohup`、`screen`、`tmux`这些工具来支持后台运行



或者使用`KPlayer`提供的程序后台运行参数来使得它在后台运行

```shell
./kplayer play start --daemon
```

运行后将会输出成功日志，这个日志仅代表`KPlayer`被正确的放到后台进行运行并且不会在前台提示任何运行期间的错误情况，所以并不代表它正在正确的在执行

```shell
INFO[2022-08-23 00:47:26] kplayer start success on daemon mode
```

当使用`daemon`模式后，所有的日志输出将会重定向到`log/kplayer.log`中，你可以查看这个文件来确定是否有异常情况发生



## 关闭KPlayer的运行

1. 使用前台运行方式时，按下`Ctrl+c`结束运行

   

2. 使用后台`Daemon`模式时，执行以下命令来结束`KPlayer` 的后台运行

```shell
./kplayer play stop
```

