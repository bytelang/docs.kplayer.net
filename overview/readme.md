## KPlayer简介

`KPlayer`是由`ByteLang Studio`设计开发的一款用于在Linux环境下进行媒体资源推流的应用程序。

只需要简单的修改配置文件即可达到开箱即用的目的，不需要了解众多推流适配、视频编解码的细节即可方便的将媒体资源在主流直播平台上进行直播。意愿是提供一个简单易上手、扩展丰富、性能优秀适合长时间不间断推流的直播推流场景。



## 提供以下基础功能

* 本地/网络视频资源的无缝推流，切换资源不导致断流
* 可自定义配置的编码参数，例如分辨率、帧率等
* 自定义多输出源，适合相同内容一次编码多路推流节省硬件资源
* 提供缓存机制避免相同内容二次编解码，大大降低在循环场景下对硬件资源的消耗
* 丰富的API接口在运行时对播放行为和资源动态控制
* 提供基础插件并具备自定义插件开发的能力
* ...



## 当前主版本

`KPlayer`目前已迭代两个大版本`v0.4.x`与`0.5.x`，其中大版本更新迭代的使用方法并不向后兼容。所以在使用与阅读本文档时请选择正确的匹配的下载文档的使用方法。点击<router-link to="/quick/install#查看当前版本号" alt="install">如何查看当前版本号</router-link>
