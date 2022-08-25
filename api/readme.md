## 简介

`KPlayer`提供API接口来提供具备编程能力的程序来控制它的资源和播放行为。在配置`rpc`功能开启后将将监听两个端口`http`与`grpc`端口，默认端口号为`http(4156)`、`grpc(4155)`。

<hr/>

 `http`是基于`grpc-gateway`插件提供数据交换。如果你具备任意语言的编码能力，你可以通过`grpc`的方式生成相应的SDK端代码直接和`grpc`端口进行通信。这通常比调用`http`接口更方便与安全



> 查看这里获取proto文件的定义规则：
>
> [https://github.com/bytelang/kplayer-go/blob/v0.5.6/proto/server/greeter.proto](https://github.com/bytelang/kplayer-go/blob/v0.5.6/proto/server/greeter.proto)