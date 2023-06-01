## 介绍

如果你想要容器化运行kplayer，我们已经把它打包为镜像，你可以方便的使用docker来运行它。

如果你担心`KPlayer`的运行对宿主机造成无法预计的影响，你可以使用Docker来运行。

如果你已经有一个kubernets集群，那使用docker也会更加方便的让你对kplayer进行管理，目前`KPlayer`支持在arm64和x86_64架构机器上使用docker来运行。



>  访问这里查看在`hub.docker.com`公开的镜像：
>
> [https://hub.docker.com/r/bytelang/kplayer](https://hub.docker.com/r/bytelang/kplayer)



## 使用方法

1. 拉取镜像

运行以下命令拉取kplayer最新版本的镜像

```shell
> docker pull bytelang/kplayer:latest
```

目前支持amd64(x86_64)与arm64(aarch64)两种架构版本上的docker运行，运行命令会匹配当前CPU架构的版本拉取到本地



2. 运行kplayer容器

在运行之前，你需要进行配置文件的自定义。运行以下命令从容器中复制出配置文件，运行后将在当前目录生成config.json文件

```shell
sudo docker run --rm --name kplayer -v $PWD:/config \
	 -it bytelang/kplayer:latest \
	 cp -p /kplayer/config.json.example  /config/config.json
```



修改该配置文件后运行容器

```shell
sudo docker run -it --name kplayer \
 -v /video:/video \
 -v $PWD/config.json:/kplayer/config.json \
 bytelang/kplayer:latest
```



`/video`目录为配置文件中配置的视频资源路径，挂载源目录与目标目录均可自定义。配置文件中需要配置容器内挂载的目标目录
