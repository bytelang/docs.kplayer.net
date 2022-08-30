## 添加插件资源

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/plugin/add" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
            "path": "show-text",
            "unique": "mytext",
            "params": {
              "text": "hello kplayer"
            }
        }'
```

**返回值**

```json
{
  "plugin": {
    "path": "plugin/show-text.kpe",
    "unique": "mytext",
    "create_time": "1661399280",
    "loaded_time": "1661399280",
    "params": {
      "text": "hello kplayer"
    }
  }
}
```



## 获取插件列表

**请求**

```shell
curl "http://127.0.0.1:4156/plugin/list" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "plugins": [
    {
      "path": "plugin/show-text.kpe",
      "unique": "mytext",
      "create_time": "1661399280",
      "loaded_time": "1661399280",
      "params": {
        "text": "hello kplayer"
      }
    }
  ]
}
```



## 更新插件参数

**请求**

```shell
curl -X "PATCH" "http://127.0.0.1:4156/plugin/update" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
        "unique": "mytext",
          "params": {
            "text": "update text"
          }
		}'
```

**返回值**

```json
{
  "plugin": {
    "path": "plugin/show-text.kpe",
    "unique": "mytext",
    "create_time": "0",
    "loaded_time": "0",
    "params": {
      "fontcolor": "white",
      "fontfile": "resource/font.ttf",
      "fontsize": "17",
      "text": "update text",
      "x": "0",
      "y": "0"
    }
  }
}
```



## 删除插件

**请求**

```shell
curl -X "DELETE" "http://127.0.0.1:4156/plugin/remove/{unique}" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "plugin": {
    "path": "plugin/show-text.kpe",
    "unique": "mytext",
    "create_time": "0",
    "loaded_time": "0",
    "params": {
      "fontcolor": "white",
      "fontfile": "resource/font.ttf",
      "fontsize": "17",
      "text": "hello kplayer",
      "x": "0",
      "y": "0"
    }
  }
}
```



