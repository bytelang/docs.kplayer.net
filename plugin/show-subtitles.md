## 介绍

自动加载视频同名文件的外挂字幕文件。支持`ass`与`srt`文件.

例如将要播放的资源路径为`/home/video.flv`，加载该插件后将会寻找同名的字幕文件`/home/video.ass`与`/home/video.srt`


::: tip 提醒
`srt`文件优先级高于`ass`
:::

不同字幕文件定义的字体不相同，如果需要完整显示。请自行下载相关字体放置至参数指定的字体目录中

## 配置文件

```json
{
  "plugin": {
    "lists": [
      {
        "path": "show-subtitles",
        "unique": "my_plugin",
        "params": {
          "fonts": "fonts",
          "alpha": "0.8"
        }
      }
    ]
  }
}
```

## 参数列表

| 参数    | 说明      | 默认值                   |
|-------|---------|-----------------------|
| fonts | 字体文件路径  | fonts                 |
| alpha | 字幕文件透明度 | 1；允许取值0.0-1.0范围值表达透明度 |

## 示例

![img](./show-subtitles.assets/img.png)