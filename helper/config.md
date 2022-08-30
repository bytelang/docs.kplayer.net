## 完整配置文件

<CodeGroup>
  <CodeGroupItem title="json" active>

```json
{
	"version": "2.0.0",
	"resource": {
		"lists": [
			"/home/user/video/起风了.flv"
		],
		"extensions": [
			"mp4"
		]
	},
	"play": {
		"start_point": 1,
		"play_model": "list",
		"encode_model": "rtmp",
		"cache_on": false,
		"cache_uncheck": false,
		"skip_invalid_resource": false,
		"fill_strategy": "tile",
		"rpc": {
			"on": true,
			"http_port": 4156,
			"grpc_port": 4157,
			"address": "127.0.0.1"
		},
		"encode": {
			"video_width": 854,
			"video_height": 480,
			"video_fps": 25,
			"audio_channel_layout": 3,
			"audio_sample_rate": 44100,
			"bit_rate": 0,
			"avg_quality": 0
		}
	},
	"output": {
		"reconnect_internal": -1,
		"lists": [{
			"path": "rtmp://127.0.0.1:1935/push",
			"unique": "test"
		}]
	},
	"plugin": {
		"lists": [{
			"path": "show-text",
			"unique": "my_plugin",
			"params": {
				"text": "hello kplayer",
				"font_size": "20"
			}
		}]
	}
}
```


  </CodeGroupItem>
  <CodeGroupItem title="yaml">

```yaml
version: 2.0.0
resource:
  lists:
    - /home/user/video/起风了.flv
  extensions:
    - mp4
play:
  start_point: 1
  play_model: list
  encode_model: rtmp
  cache_on: false
  cache_uncheck: false
  skip_invalid_resource: false
  fill_strategy: tile
  rpc:
    'on': true
    http_port: 4156
    grpc_port: 4157
    address: 127.0.0.1
  encode:
    video_width: 854
    video_height: 480
    video_fps: 25
    audio_channel_layout: 3
    audio_sample_rate: 44100
    bit_rate: 0
    avg_quality: 0
output:
  reconnect_internal: -1
  lists:
    - path: 'rtmp://127.0.0.1:1935/push'
      unique: test
plugin:
  lists:
    - path: show-text
      unique: my_plugin
      params:
        text: hello kplayer
        font_size: '20'

```

  </CodeGroupItem>
</CodeGroup>


