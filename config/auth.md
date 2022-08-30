## 完整配置文件

`KPlayer`的配置文件顶级中的`auth`用于配置主程序针对`rpc`接口的鉴权权限。

该参数开启时，任何客户端调用`rpc`或者`http`端口时都需要携带配置项的token，否则将会拒绝服务



<CodeGroup>
  <CodeGroupItem title="json" active>

```json
{
  "auth": {
    "auth_on": false,
    "token": "kplayer"
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml
auth:
  auth_on: false
  token: kplayer
```

  </CodeGroupItem>
</CodeGroup>

## 开启auth

<CodeGroup>
  <CodeGroupItem title="json" active>

```json {3}
{
  "auth": {
    "auth_on": false
  }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {2}
auth:
  auth_on: false
```

  </CodeGroupItem>
</CodeGroup>



`KPlayer`默认关闭auth功能，使用当前选项开启鉴权功能



## 设置Token





<CodeGroup>
  <CodeGroupItem title="json" active>

```json {3}
{
    "auth": {
        "token": "kplayer"
    }
}
```

  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml {2}
auth:
  token: kplayer
```

  </CodeGroupItem>
</CodeGroup>



## 使用方法

在正确配置`auth`相关接口后，在使用http或者grpc方法需要携带token值

* 使用`http`接口示例需要携带`Authorization: {token}`

```shell
curl "http://127.0.0.1:4156/resource/list" \
     -H 'Authorization: kplayer' \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```



<br/>

* 使用`grpc`接口需要携带metadata的key为`authorization`名称，value为`token`的元数据