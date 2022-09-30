## 完整配置文件

`KPlayer`的配置文件顶级中的`resource`用于配置输入资源相关参数。以下是完整的资源配置项

<CodeGroup>
  <CodeGroupItem title="json" active>

```json
{
  "resource": {
    "lists": [
      {
        "unique": "main-res",
        "seek": 10,
        "end": 20,
        "groups": [
          {
            "path": "/home/user/video/起风了.flv",
            "media_type": "video",
            "persistent_loop": true
          },
          {
            "path": "/home/user/video/music.mp3",
            "media_type": "audio"
          }
        ]
      },
      "/home/user/video/起风了.flv",
      "/home/user/video"
    ],
    "extensions": [
      "mp4",
      "flv"
    ]
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml
resource:
  lists:
    - unique: main-res
      seek: 10
      end: 20
      groups:
        - path: /home/user/video/起风了.flv
          media_type: video
          persistent_loop: true
        - path: /home/user/video/music.mp3
          media_type: audio
    - /home/user/video/起风了.flv
    - /home/user/video
  extensions:
    - mp4
    - flv


```

  </CodeGroupItem>
</CodeGroup>

## 配置资源列表

<CodeGroup>
  <CodeGroupItem title="json" active>

```json {3-21}
{
	"resource": {
		"lists": [
		   {
              "unique": "main-res",
              "seek": 10,
              "end": 20,
              "groups": [
                {
                  "path": "/home/user/video/起风了.flv",
                  "media_type": "video",
                  "persistent_loop": true
                },
                {
                  "path": "/home/user/video/music.mp3",
                  "media_type": "audio"
                }
              ]
           },
			"/home/user/video/起风了.flv",
			"/home/user/video"
		]
	}
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {2-4}
resource:
  lists:
    - /home/user/video/起风了.flv
    - /home/user/video

```

  </CodeGroupItem>
</CodeGroup>


`lists`配置项为数组类型，允许支持多种协议。包括以下协议：

* `file://`


* `rtmp://`


* `http(s)://`


* `ftp://`

若未标明`uri`协议类型默认使用`file://` 协议进行。所以，你也可以使用网络文件来配置视频输入


<CodeGroup>
  <CodeGroupItem title="json" active>

```json {4-6}
{
	"resource": {
		"lists": [
			"/home/user/video/起风了.flv",
			"http://127.0.0.1/起风了.flv",
			"ftp://127.0.0.1/起风了.flv"
		]
	}
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {3-5}
resource:
  lists:
    - '/home/user/video/起风了.flv'
    - 'http://127.0.0.1/起风了.flv'
    - 'ftp://127.0.0.1/起风了.flv'

```

  </CodeGroupItem>
</CodeGroup>

## 高阶资源配置

高阶资源配置可以对资源进行扩展配置，并兼容当前列表方式的资源编写方式，因此也可以将不同类型的配置混用

例如

```json {4,6-9,12-25,27}
{
  "resource": {
    "lists": [
      "/home/user/video/起风了.flv",
      {
        "unique": "qfl-res",
        "path": "/home/user/video/起风了.flv",
        "seek": 10,
        "end": 20
      },
      {
        "unique": "qfl-res",
        "seek": 10,
        "end": 20,
        "groups": [
          {
            "path": "/home/user/video/background.png",
            "media_type": "video",
            "persistent_loop": true
          },
          {
            "path": "/home/user/video/music.mp3",
            "media_type": "audio"
          }
        ]
      },
      "/home/user/video/起风了-(2).flv"
    ]
  }
}
```

#### 配置单资源属性

`KPlayer`现在支持对推流资源的的更多属性进行设置

如果你想要使用此项功能，你需要定义更多的自定义选项。例如下方

```json {4-9}
{
  "resource": {
    "lists": [
      {
        "unique": "main-res",
        "path": "/home/user/video/起风了.flv",
        "seek": 10,
        "end": 20
      }
    ]
  }
}
```

<br/>

由于`lists`是一个数组类型，配置项中表明了需要被定义的属性：

| 参数 | 子配置 | 说明 | 必填 | 默认值 |
|----|----| -- | --- | --- |
| unique |-| 自定义资源唯一标识名称 | 否| 自动分配 |
| path |-| 资源文件路径 | 是 | - |
| seek |-| 从资源的多少s(秒)起始播放 | 否| 0 |
| end |-| 播放到视频资源的多少s(秒)后停止 | 否| -1 |

<br/>

::: tip 提醒
路径必须显式指定每个资源的完整路径，不支持文件夹方式
:::

#### 配置混合资源属性

`KPlayer`现在支持对推流资源的音频和视频资源流分别指定不同的资源来配置。

它可以用于来支持将纯音频文件配合图片或者视频资源来作为画面的输出流来显示，或者在未音频流的视频资源上添加推流的背景音乐。

如果你想要使用此项功能，你需要定义更多的自定义选项。例如下方

```json {4-19}
{
  "resource": {
    "lists": [
      {
        "unique": "main-res",
        "seek": 10,
        "end": 20,
        "groups": [
          {
            "path": "/home/user/video/起风了.flv",
            "media_type": "video",
            "persistent_loop": true
          },
          {
            "path": "/home/user/video/music.mp3",
            "media_type": "audio"
          }
        ]
      }
    ]
  }
}
```

<br/>

由于`lists`是一个数组类型，这仅仅只是定义个一个需要推流播放的资源对象。配置项中表明了需要被定义的属性：

| 参数 | 子配置 | 说明 | 必填 | 默认值 |
|----|----| -- | --- | --- |
| unique |-| 自定义资源唯一标识名称 | 否| 自动分配 |
| seek |-| 从资源的多少s(秒)起始播放 | 否| 0 |
| end |-| 播放到视频资源的多少s(秒)后停止 | 否| -1 |
| groups |-| 定义当为混合资源时，它需要的资源组 | 是 | - |
| | path | 资源路径 | 是 | - |
| | media_type | 资源类型 | 是，支持`video`和`audio`两项 | - |
| | persistent_loop | 保持持续的循环 | 否 | false |

<br/>

::: tip 提醒
示例中作为混合资源的配置项

它将会选取`/home/user/video/起风了.flv`的视频画面并选取`/home/user/video/music.mp3`为音频资源来进行推流

并且在完成音频文件时长后会结束当前资源的播放
:::

<br/>

混合类型资源存在主资源的设计，默认情况下若未指定资源的`persistent_loop`字段则会选择视频资源作为主资源

它会直接影响到当前播放资源的日志打印，并且在通过Cli或者API获取播放详情会以主资源来作为主要信息来返回

主资源选择策略:

1. 视频和音频均为设置持续循环，视频资源为主资源
2. 视频和音频其中之一设置持续循环，不需要循环的资源未主资源。（例如视频是png资源，音频为mp3资源。音频为主资源类型）
3. 视频和音频均设置持续循环，视频资源未主资源

<br/>

**资源的总长度和主资源的选择策略有关，始终将会以主资源的时长作为当前混合资源的总时长。**

**当主资源播放完成后将会立即结束当前资源的播放。**

::: tip 提醒
混合资源必须显式指定每个资源的完整路径，不支持文件夹方式
:::

## 配置文件夹路径

<CodeGroup>
  <CodeGroupItem title="json" active>

```json {6}
{
  "resource": {
    "lists": [
			"/home/user/video/"
		],
    "extensions": [ "mp4", "flv" ]
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {4-6}
resource:
  lists:
    - /home/user/video/
  extensions:
    - mp4
    - flv
```

  </CodeGroupItem>
</CodeGroup>



默认情况下`lists`中必须填写完整的可读文件路径，除此之外还允许配置**文件夹路径**
。但是通常情况下文件夹中会掺杂不符合期望的文件类型，使用`exstensions`配置来指明只检索匹配该类型后缀的文件

::: tip 提醒

文件夹和完整文件路径可以混合使用

:::

以下的配置只会检索`/home/user/video/`下文件后缀为`mp4`与`flv`的文件并将他们添加至播放列表中

当配置文件夹时，文件夹的列表使用字典排序来确定播放顺序。如果无法达到预期的播放顺序尝试对文件的首字母进行`00-99`和`a-z`
排序来确保播放顺序。或者显示填写每一个资源的播放顺序