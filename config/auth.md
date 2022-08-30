## 完整配置文件

`KPlayer`的配置文件顶级中的`auth`用于配置主程序针对`rpc`接口的鉴权权限。

该参数开启时，任何客户端调用`rpc`或者`http`端口时都需要携带配置项的token，否则将会拒绝服务

```json
{
  "auth": {
    "auth_on": false,
    "token": "kplayer"
  }
}
```

## 开启auth



```json {4-11}
{
  "auth": false
}
```



`KPlayer`默认关闭auth功能，使用当前选项开启鉴权功能



## 设置Token



```json {4-11}
{
  "token": "kplayer"
}
```



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