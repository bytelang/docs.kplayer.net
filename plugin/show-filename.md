## 介绍

在视频上指定位置显示当前播放文件名

## 配置文件

```json
{
  "plugin": {
    "lists": [
      {
        "path": "show-filename",
        "unique": "my_plugin",
        "params": {
          "fontcolor": "red"
        }
      }
    ]
  }
}
```



## 参数列表

| 参数           | 说明                                                         | 默认值            |
| -------------- | ------------------------------------------------------------ | ----------------- |
| fontsize       | 字体大小                                                     | 17                |
| fontcolor      | 字体颜色，支持常用颜色(red,white,black...)与RGB十六进制颜色值 | white             |
| fontfile       | 字体文件                                                     | resource/font.ttf |
| x              | 以视频左上角为原点的横坐标，最大可视范围为分辨率宽           | 0                 |
| y              | 以视频左上角为原点的纵坐标，最大可视范围为分辨率高           | 0                 |
| show_extension | 是否显示文件扩展名                                           | false             |



## 示例

![image-20220825135221559](./show-filename.assets/image-20220825135221559.png)