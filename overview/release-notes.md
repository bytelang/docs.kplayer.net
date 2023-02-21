## 版本更新内容


1. 新增<router-link to="/api/play.html#更改当前编码平均质量">API接口</router-link>方法提供运行中变更视频质量参数，可以进行动态控制输出比特率大小

2. 新增获取当前配置编码参数信息<router-link to="/api/play.html#获取当前编码信息">API接口</router-link>

3. 调整画质质量参数`avg_quality`最大值为30，提供调整更低的画质参数

4. 缩短编码后视频关键帧间隔大小，优化推流解析速度

5. 调整视频解码解析策略，允许输入视频个别不符合编码标准的帧进行跳过处理。解决解码过程中报错 （Invalid data found when processing input [-1094995529]）

6. 修复图片、音频混合资源方式比特率过大的异常

7. 修复在配置`cache_uncheck: true`时正确命中缓存文件后仍然检查源文件的问题

8. 修复在配置`auth`功能后，无法正常使用`cli`的异常问题

9. 修复在较低Linux内核发行版本上触发`panic: getrandom failed`的问题
