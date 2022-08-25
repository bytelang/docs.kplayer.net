## 添加输出资源

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/output/add" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
          "path": "/home/user/video/起风了.flv"
        }'
```

**返回值**

```json
{
  "output": {
    "path": "/home/user/video/起风了.flv",
    "unique": "mMRzUj"
  }
}
```



## 删除输出资源

**请求**

```shell
curl -X "DELETE" "http://127.0.0.1:4156/output/remove/{unique}" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "output": {
    "path": "/home/user/video/起风了.flv",
    "unique": "mMRzUj"
  }
}
```



## 获取输出资源列表

**请求**

```shell
curl "http://127.0.0.1:4156/output/list" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```shell
{
  "outputs": [
    {
      "path": "rtmp://127.0.0.1:1935/live/test",
      "unique": "33f043",
      "create_time": "1661398487",
      "end_time": "0",
      "start_time": "1661398487",
      "connected": true
    }
  ]
}
```