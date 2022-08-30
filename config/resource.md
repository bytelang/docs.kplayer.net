## 完整配置文件

`KPlayer`的配置文件顶级中的`resource`用于配置输入资源相关参数。以下是完整的资源配置项

```json
{
	"resource": {
		"lists": [
			"/home/user/video/起风了.flv",
			"/home/user/video"
		],
		"extensions": [
			"mp4", "flv"
		]
	}
}
```



## 配置资源列表

```json {3-6}
{
	"resource": {
		"lists": [
			"/home/user/video/起风了.flv",
			"/home/user/video"
		]
	}
}
```

`lists`配置项为数组类型，允许支持多种协议。包括以下协议：

* `file://`

  

* `rtmp://`

  

* `http(s)://`

  

* `ftp://`



若未标明`uri`协议类型默认使用`file://` 协议进行。所以，你也可以使用网络文件来配置视频输入

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



## 配置文件夹路径



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



默认情况下`lists`中必须填写完整的可读文件路径，除此之外还允许配置**文件夹路径**。但是通常情况下文件夹中会掺杂不符合期望的文件类型，使用`exstensions`配置来指明只检索匹配该类型后缀的文件



::: tip 提醒

文件夹和完整文件路径可以混合使用

:::



以下的配置只会检索`/home/user/video/`下文件后缀为`mp4`与`flv`的文件并将他们添加至播放列表中

当配置文件夹时，文件夹的列表使用字典排序来确定播放顺序。如果无法达到预期的播放顺序尝试对文件的首字母进行`00-99`和`a-z`排序来确保播放顺序。或者显示填写每一个资源的播放顺序