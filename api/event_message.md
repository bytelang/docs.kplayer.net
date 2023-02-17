## 事件订阅介绍

`KPlayer`的整个生命周期的行为全都围绕着消息事件来驱动

其中包含了`Prompt`类型的**命令类事件**例如

* `EVENT_PROMPT_ACTION_OUTPUT_ADD`事件用来标识需要添加一个额外的输出资源，
* `EVENT_PROMPT_ACTION_RESOURCE_ADD`表示需要添加新的播放资源事件

消息通知类型的**通知类事件**例如

* `EVENT_MESSAGE_ACTION_PLAYER_STARTED`事件用来通知程序已经初始化完成开始播放
* `EVENT_MESSAGE_ACTION_RESOURCE_START`事件用来通知某个资源正在被开始播放

## 订阅通知类事件

在开启了`rpc`功能后，`KPlayer`提供了通过http接口的websocket协议来订阅发生的所有事件

*订阅地址：*

```javascript
ws://127.0.0.1:4156/websocket
```

你可以使用你熟悉的任何语言的websocket库来进行连接获取到消息事件

## 事件格式

`KPlayer`
的数据结构定义依赖protobuf的定义结构

在这里[https://github.com/bytelang/libkplayer-proto](https://github.com/bytelang/libkplayer-proto)
查看到所有的消息类型定义和它们的数据结构

包含了所有生命周期内可能会接收到的所有消息
```javascript
enum EventMessageAction {
  // ----------------------------------
  // define message action
  // broadcast message action from kplayer core
  // ----------------------------------

  // player
  EVENT_MESSAGE_ACTION_PLAYER_STARTED = 0;
  EVENT_MESSAGE_ACTION_PLAYER_PAUSE = 1;
  EVENT_MESSAGE_ACTION_PLAYER_CONTINUE = 2;
  EVENT_MESSAGE_ACTION_PLAYER_SKIP = 3;
  EVENT_MESSAGE_ACTION_PLAYER_ENDED = 4;
  EVENT_MESSAGE_ACTION_PLAYER_STOP = 21;

  // resource
  EVENT_MESSAGE_ACTION_RESOURCE_START = 5;
  EVENT_MESSAGE_ACTION_RESOURCE_FINISH = 6;
  EVENT_MESSAGE_ACTION_RESOURCE_EMPTY = 7;
  EVENT_MESSAGE_ACTION_RESOURCE_REMOVE = 8;
  EVENT_MESSAGE_ACTION_RESOURCE_ADD = 9;
  EVENT_MESSAGE_ACTION_RESOURCE_LIST = 10;
  EVENT_MESSAGE_ACTION_RESOURCE_CURRENT = 11;
  EVENT_MESSAGE_ACTION_RESOURCE_CHECKED = 20;
  EVENT_MESSAGE_ACTION_RESOURCE_SEEK = 22;

  // output
  EVENT_MESSAGE_ACTION_OUTPUT_ADD = 12;
  EVENT_MESSAGE_ACTION_OUTPUT_REMOVE = 13;
  EVENT_MESSAGE_ACTION_OUTPUT_LIST = 14;
  EVENT_MESSAGE_ACTION_OUTPUT_DISCONNECT = 15;

  // plugin
  EVENT_MESSAGE_ACTION_PLUGIN_ADD = 16;
  EVENT_MESSAGE_ACTION_PLUGIN_REMOVE = 17;
  EVENT_MESSAGE_ACTION_PLUGIN_LIST = 18;
  EVENT_MESSAGE_ACTION_PLUGIN_UPDATE = 19;
}
```