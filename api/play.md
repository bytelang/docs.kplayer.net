## 获取当前版本信息

**请求**

```shell
curl "http://127.0.0.1:4156/play/information" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "major_version": "v0.5.6",
  "libkplayer_version": "v1.4.14",
  "plugin_version": "1.5.1",
  "license_version": "v1",
  "start_time": "2022-08-24 16:33:24.346563091 +0800 CST m=+3.296453592",
  "start_time_timestamp": "1661330004"
}
```

## 获取运行时长

**请求**

```shell
curl "http://127.0.0.1:4156/play/duration" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "start_timestamp": "1661397635",
  "duration_timestamp": "14"
}
```

## 结束播放

`KPlayer` 并不直接提供API接口达成远程结束进程的能力。

此处的结束播放适用于当`play_model`为`queue`模式时，主程序当队列为空时等待新的资源进入，调用当前API立即停止队列等待结束主程序。

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/play/stop" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```shell
{}
```

## 暂停播放

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/play/pause" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{}
```

## 继续播放

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/play/continue" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{}
```

## 跳过当前播放资源

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/play/skip" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{}
```

## 获取当前编码信息

**请求**

```shell
curl "http://127.0.0.1:4156/play/encode" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{}'
```

**返回值**

```json
{
  "video_width": 854,
  "video_height": 480,
  "video_fps": "25",
  "audio_channel_layout": 3,
  "audio_sample_rate": 44100,
  "bit_rate": "0",
  "avg_quality": "0"
}
```

## 更改当前编码平均质量

::: tip 提醒
该接口仅在未指定`bit_rate`固定值参数时生效，并且不会在使用缓存并命中缓存文件时生效
:::

**请求**

```shell
curl -X "POST" "http://127.0.0.1:4156/play/encode/avg_quality" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -d $'{
  "avg_quality": 30
}'
```

**返回值**

```json
{}
```