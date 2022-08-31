## 版本更新内容

1. 添加配置文件中指定play_mode中的列表随机random与队列queue模式 #37

2. 添加自适应分辨率参数选项fill_strategy用来配置设置分辨率与源视频分辨率不一致时的缩放策略。支持tile按比例拉伸、ratio自适应比例进行黑色背景填充
3. 升级插件版本至v1.5.0。提供插件中允许嵌套子插件的功能、提供插件初始化完成回调函数、允许自定义可修改参数白名单 #38
4. 添加输出与插件资源前置加载问题，解决插件异步加载造成的加载延迟的问题。添加插件按照当前配置文件顺序加载 #35
5. 添加插件管理器模块，以适应不用版本插件版本的差异化加载
6. 修复生成缓存再某些条件下效率异常的问题 #42
7. 修复在使用缓存输出时，输出资源列表断开或为空时内存泄漏问题
8. 修复在使用缓存进行推流播放时再某些C版本标准库时造成的内存泄漏，长时间内存占用过大触发Killed的错误
9. 优化输入资源UniqueName的生成策略，使得同名同路径资源文件unique始终不变
10. 优化音视频同步策略，解决采用flv.js（例如bilibili网页版）等库的兼容性。提高推流流畅性