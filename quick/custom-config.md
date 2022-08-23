## 创建配置文件

在上一步安装顺利后，在kplayer目录中将存在config.json.example，它是一个最简版本用来支持推流的配置文件。你可以选择自己创建文件或者将它复制一份成为新的配置文件。

使用`cp`命令重命名并复制一份配置文件

```shell
cp config.json.example config.json
```



::: tip 提醒

`KPlayer`默认的配置文件名称为`config.json`优先在`homedir`目录中查找该配置文件。（*homedir* [请参考这里]( #)）

:::



## 修改配置文件

打开`config.json`文件，可以看到预置的一些配置项

```json
{
    "version": "2.0.0",
    "resource": {
        "lists": [
            "/video/example_1.mp4",
            "/video/example_2.mp4"
        ]
    },
    "output": {
        "lists": [
            {
                "path": "rtmp://127.0.0.1:1935/push"
            }
        ]
    }
}
```



#### 修改视频资源路径

基于这个配置文件，你只需要改动很少的一部分配置即可完成资源推流

修改视频资源目录至你的视频文件路径，假设你的视频文件路径为`/home/user/video/起风了.flv`

```json {5}
{
    "version": "2.0.0",
    "resource": {
        "lists": [
            "/home/user/video/起风了.flv"
        ]
    },
    "output": {
        "lists": [
            {
                "path": "rtmp://127.0.0.1:1935/push"
            }
        ]
    }
}
```



#### 修改推流地址

1. 推流地址是将要把视频资源的画面与声音推送给服务端的通信地址，如果是像bilibili、虎牙、斗鱼....等直播平台通常是需要在个人中心并**开启直播**后，将会得到`推流地址`与`推流码`。将推流码追加至推流地址后即可得到推流地址

2. 自己搭建推流服务器，通过很多开源工具也可以很方便的搭建推流服务器。推荐使用[https://github.com/arut/nginx-rtmp-module](https://github.com/arut/nginx-rtmp-module)与[https://github.com/illuspas/Node-Media-Server](https://github.com/illuspas/Node-Media-Server)快速的搭建推流服务端

假设推流地址为`rmtp://127.0.0.1:1935/live/test`，使用获取到的新的推流地址修改至配置文件中

```json {11}
{
    "version": "2.0.0",
    "resource": {
        "lists": [
            "/home/user/video/起风了.flv"
        ]
    },
    "output": {
        "lists": [
            {
                "path": "rmtp://127.0.0.1:1935/live/test"
            }
        ]
    }
}
```





## 配置文件修改完成

::: tip 提醒



:::

完成上述两步，确保你填写的视频文件地址正确无误与推流地址无误。恭喜你，你完成最简版的配置文件的修改。

