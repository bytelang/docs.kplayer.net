## 完整配置文件

`KPlayer`的配置文件顶级中的`output`用于配置输出资源相关参数。以下是完整的配置项

<CodeGroup>
  <CodeGroupItem title="json" active>

```json
{
  "output": {
    "reconnect_internal": -1,
    "lists": [
      {
        "path": "rtmp://127.0.0.1:1935/push",
        "unique": "test"
      }
    ]
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml
output:
  reconnect_internal: -1
  lists:
    - path: 'rtmp://127.0.0.1:1935/push'
      unique: test
```

  </CodeGroupItem>
</CodeGroup>



## 重连间隔时间

<CodeGroup>
  <CodeGroupItem title="json" active>

```json {3}
{
  "output": {
    "reconnect_internal": 5
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {2}
output:
  reconnect_internal: 5
```

  </CodeGroupItem>
</CodeGroup>



`reconnect_internal`  配置输出地址终端断开连接的情况下是否进行重连尝试。当与推流服务端断开连接时触发的默认行为将会结束主程序，配置此项在推流服务端断开时间隔多少秒后不断重试。

| 值                 | 说明     | 默认值 |
| ------------------ | -------- | ------ |
| reconnect_internal | 单位为秒 | -1     |



## 输出地址列表




<CodeGroup>
  <CodeGroupItem title="json" active>

```json {3-8}
{
  "output": {
    "lists": [
      {
        "path": "rtmp://127.0.0.1:1935/push",
        "unique": "test"
      }
    ]
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {2-4}
output:
  lists:
    - path: 'rtmp://127.0.0.1:1935/push'
      unique: test
```

  </CodeGroupItem>
</CodeGroup>



`KPlayer`默认支持多输出资源，视频资源编解码一次同样内容推流至多个推流服务端。这种情况下编解码资源只会占用一份，多个输出资源大部分占用的是带宽资源。



| 值    | 子项   | 说明                                            | 默认值 |
| ----- | ------ | ----------------------------------------------- | ------ |
| lists | -      | 数组类型                                        | -      |
|       | path   | 推流地址                                        | -      |
|       | unique | 推流对象的唯一id，该id作为API功能的全局唯一名称 | 可选   |



`unique`可自定义或由`KPlayer`随机生成。因为存在多个输出资源，这个值用于通过API接口来确定输出对象的唯一ID参数


