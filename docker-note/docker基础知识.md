# docker学习
学习来源：[Docker 入门教程 - 阮一峰的网络日志](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
> 现有的环境解决方案：
1. 虚拟机：占用资源多，冗余步骤多，启动慢
2. Linux 容器 启动快，资源占用少，体积小

> 什么是docker 
doker属于Linux 容器的一种封装，目前最流行的 Linux 容器解决方案
docker将应用程序和该程序的依赖放在一个包里

> Docker 的用途：
1. 提供一次性的环境
2. 提供弹性的云服务
3. 组建微架构服务器

> Docker 的版本
社区版（Community Edition ，CE）
企业版（Enterprise Edition ，EE）

> image 文件
docker 将应用及其依赖打包在 image 文件里。只有通过这个文件才能生成docker容器。image可以看成是容器的模板。docker根据哦，image生成容器的实例。同一个image可以生成多个同时运行的容器。

image 是二进制文件，实际开发中，一个image文件往往通过继承另一个image文件，加上一些个性化设置而生成。(例如在ubuntu的image中加入了apache并保存成自己的image)

```
#local image list
$docker image ls

#delete image file
$docker image rm [imageName]
```

image 可以去官方仓库中找到自己需要的。

```
#get image
$docker image pull

#eg library 是image是文件所在的组，hello-world 是image文件的名字
$docker image pull library/hello-world

#docker的官方组是 library
#抓取成功可以运行 docker image ls 来查看 image 文件

#运行这个image文件
$docker container run hello-world
```

`docker container run` 命令会从image生成正在运行的容器实例。
如果发现本地没有指定的 image 文件，以上命令会从仓库自动抓取。
故 `docker image pull` 命令并不是必须步骤。

比如如下命令可以体验一个完整的ubuntu image :
`docker container run -it ubuntu bash`

对于不会自动终止的容器，必须使用 docker container kill 命令手动终止
`docker container kill [containID]`

> 容器文件
image 文件生成的容器实例，本身也是个文件，成为容器文件。
一旦容器生成，会同时存在两个文件：image 文件和容器文件。
关闭容器并不会删除容器文件，只是容器停止运行而已。

```
# 列出正在运行的容器
$ docker container ls

# 列出本机所有容器，包括终止运行的容器
$ docker container ls --all

# 根据id删除容器文件(docker container kill 命令终止容器文件依然会占用磁盘空间)
$ docker container rm [containerID]
```

> Dockerfile 文件
Dockerfile 是一个文本文件，用来配置 image。 Docker 根据该二进制 image 文件。

