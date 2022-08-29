## 完整配置文件

`KPlayer`的配置文件顶级中的`plugin`用于配置插件资源相关参数。以下是完整的配置项

::: tip 提醒
lists为数组类型，若需要添加多个插件扩充lists数组对象即可
:::

```json
{
  "plugin": {
    "lists": [
      {
        "path": "show-text",
        "unique": "my_plugin",
        "params": {
          "text":"hello kplayer",
          "font_size": "20"
        }
      }
    ]
  }
}
```

## 插件地表

`KPlayer`支持自定义插件来扩展视频资源的展现方式。包括向视频资源上添加自定义文件、添加水印图片...等等插件。以下是配置插件的格式，具体数据由插件的基础属性决定。



| 值    | 子项   | 说明                                                         | 默认值 |
| ----- | ------ | ------------------------------------------------------------ | ------ |
| lists | -      | 数组类型                                                     | -      |
|       | path   | 插件名称，将会已名称匹配plugin目录下{path}.kpe插件文件。若是被收录的插件，将会在加载之前自动下载至plugin目录中 | -      |
|       | unique | 推流对象的唯一id，该id作为API功能的全局唯一名称              | 可选   |
|       | params | 需要给插件传递的参数，对象key-value类型。具体含义由插件的具体实现决定 | -      |



以下用在推流资源显示指定文本插件为例

`unique`可自定义或由`KPlayer`随机生成。因为存在多个插件资源，这个值用于通过API接口来确定输出对象的唯一ID参数



```json {4-11}
{
  "output": {
    "lists": [
      {
        "path": "show-text",
        "unique": "my_plugin",
        "params": {
          "text":"hello kplayer",
          "font_size": "20"
        }
      }
    ]
  }
}
```

## 加载多个插件

加载多个插件，需要保证插件的各自`unique`唯一不重复
```json
{
  "plugin": {
    "lists": [
      {
        "path": "show-text",
        "unique": "my_plugin",
        "params": {
          "text":"hello kplayer",
          "font_size": "20"
        }
      },
      {
        "path": "show-text",
        "unique": "my_plugin-2",
        "params": {
          "text":"hello kplayer-2",
          "font_size": "20"
        } 
      }
    ]
  }
}
```

## 插件匹配方式

`KPlayer`提供基础的ServerAPI来降低使用复杂度。并且我们支持将已被收录的插件通过api的方式进行分发下载。

在配置项中配置`path`值会优先通过ServerAPI来查找是否匹配该插件，若该名称已被收录则会自动下载插件至`homedir`目录的`plugin` 目录中

如果插件未第三方分发未被收录，则你需要手动下载文件扩展名为`kpe`的文件至`plugin`目录中