## 增加输入资源

**请求**

| 参数   | 说明             | 必填 |
| ------ | ---------------- | ---- |
| path   | 输入视频资源地址 | 是   |
| unique | unique唯一ID     | 否   |



```shell
curl -X "POST" "http://127.0.0.1:4156/resource/add" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
             "path": "/home/user/video/起风了.flv",
             "unique": "test"
         }'
```

**返回值**

```json
{
  "path": "/home/user/video/起风了.flv",
  "unique": "test"
}
```



## 获取完整列表资源

**请求**

```shell
curl "http://127.0.0.1:4156/resource/list-all" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "resources": [
    {
      "path": "/home/user/video/起风了.flv",
      "unique": "mMRzUj",
      "seek": "0",
      "end": "-1",
      "create_time": "1661337418",
      "start_time": "1661337418",
      "end_time": "1661337744"
    }
  ]
}
```



## 获取未播放列表

**请求**

```shell
curl "http://127.0.0.1:4156/resource/list" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "resources": [
    {
      "path": "/home/user/video/起风了.flv",
      "unique": "mMRzUj",
      "seek": "0",
      "end": "-1",
      "create_time": "1661337418",
      "start_time": "1661337418",
      "end_time": "1661337744"
    }
  ]
}
```



## 获取当前播放资源

**请求**

```shell
curl "http://127.0.0.1:4156/resource/current" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "resource": {
    "path": "/home/user/video/起风了.flv",
    "unique": "mMRzUj",
    "seek": "0",
    "end": "0",
    "create_time": "1661396962",
    "start_time": "1661396963",
    "end_time": "0"
  },
  "duration": "325",
  "duration_format": "0:5:25",
  "seek": "9",
  "seek_format": "0:0:9",
  "hit_cache": false
}
```

| 参数            | 说明                         |
| --------------- | ---------------------------- |
| resource        | 资源基础信息                 |
| duration        | 视频资源总长度               |
| duration_format | 视频资源总长度格式化时间     |
| seek            | 当前播放时间                 |
| seek_format     | 当前播放时间格式化时间       |
| hit_cache       | 是否命中缓存使用缓存正在播放 |



## 删除输入资源

**请求**

```shell
curl -X "DELETE" "http://127.0.0.1:4156/resource/remove/{unique}" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "resource": {
    "path": "/home/user/video/起风了.flv",
    "unique": "mMRzUj",
    "create_time": "1661396962"
  }
}
```



## 资源时间跳转

**请求**

| 参数   | 说明                   | 必填 |
| ------ | ---------------------- | ---- |
| unique | unique唯一ID           | 是   |
| seek   | 目标跳转资源的起始秒数 | 是   |



```shell
curl -X "POST" "http://127.0.0.1:4156/resource/seek" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
            "unique": "mMRzUj",
            "seek": "10"
        }'
```

**返回值**

```json
{
  "resource": {
    "path": "/home/user/video/起风了.flv",
    "unique": "mMRzUj",
    "seek": "10",
    "end": "0",
    "create_time": "1661396962",
    "start_time": "1661397299",
    "end_time": "0"
  }
}
```

