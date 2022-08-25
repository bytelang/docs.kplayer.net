## 介绍

用于实现 KPlayer 推流过程中在指定位置显示系统当前时间，因为推流存在时间差，显示的时间将会有延迟

## 配置文件

```json
{
  "plugin": {
    "lists": [
      {
        "path": "show-time",
        "unique": "my_plugin",
        "params": {
          "fontsize": "20",
          "fontcolor": "red"
        }
      }
    ]
  }
}
```



## 参数列表

| 参数      | 说明                                                         | 默认值            |
| --------- | ------------------------------------------------------------ | ----------------- |
| fontsize  | 字体大小                                                     | 17                |
| fontcolor | 字体颜色，支持常用颜色(red,white,black...)与RGB十六进制颜色值 | white             |
| fontfile  | 字体文件                                                     | resource/font.ttf |
| x         | 以视频左上角为原点的横坐标，最大可视范围为分辨率宽           | 0                 |
| y         | 以视频左上角为原点的纵坐标，最大可视范围为分辨率高           | 0                 |



## 示例

![image-20220825141600932](./show-time.assets/image-20220825141600932.png)