@[图文并茂基于CentOS Linux release 7.8.2003 Core安装并Docker化你的Node.js应用:watermelon:](https://github.com/tangdou369098655/docker/edit/master/README.md)


:cherry_blossom:简体中文:cherry_blossom: | [English](https://github.com/tangdou369098655/docker/blob/master/README_ENG.md)

## 说明:cherries:
* 本文介绍如何在CentOS Linux release 7.8.2003部署并使用Docker。
* 旨在使用最简单快速的办法，:smirk:解决使用docker部署nodejs需求&#x1F353;。

## :cherry_blossom::cherry_blossom::cherry_blossom::cherry_blossom::cherry_blossom::cherry_blossom:

## 前提:cherries:
>你要有一个服务器哟~~
>购买后打开就像这个下面这个样子:grin:


![在这里插入图片描述](https://img-blog.csdnimg.cn/2020052418024250.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
## 备注:cherries:
- :cherry_blossom:因为本来用的是阿里云服务器进行安装，Aliyun Linux 2.1903 LTS 64位操作系统的ECS实例，后期遇到一些问题，查詢很多資料按照資料操作，但是問題暂时还未解决，所以用了同事的服务器进行再次安装:grin:
- 具体配置情况如下
- &#x1F353;查看Linux 内核&#x1F353;

```bash
uname -a
cat /proc/version
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630222141221.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
- 查看当前系统版本的详细信息

```bash
1.cat /etc/redhat-release(此方法只适合Redhat 系的Linux)
2.lsb_release -a (此命令适用于所有的Linux 发行版本）
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630222951679.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
## 步骤一：链接服务器:cherry_blossom:
1. 链接成功后如下图所示，如果不知道如何链接，可以参考（https://github.com/tangdou369098655/FrontEndDeployment/blob/master/nginx_zh.md）:cherries:
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200524181539512.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
2. 依次运行以下命令添加yum源。:cherries:

```bash
yum update
yum install epel-release -y
yum clean all
yum list
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628152434129.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020062815254713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628152838135.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628152912139.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628152946921.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

3. 安装并运行Docker。:cherries:

```bash
yum install docker-io -y
systemctl start docker
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153130693.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153143730.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153644197.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

4. 解决报错，查看错误信息：:cherries:(備註，如果你用的CentOS Linux可以直接跳過這一步，一般沒有下面問題)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153838790.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

```bash
[root@iZ2ze67ifeuz62igol9apzZ ~]# docker -v
Docker version 1.13.1, build 4ef4b30/1.13.1
[root@iZ2ze67ifeuz62igol9apzZ ~]#  systemctl status docker.service -l
● docker.service - Docker Application Container Engine
   Loaded: loaded (/usr/lib/systemd/system/docker.service; disabled; vendor preset: disabled)
   Active: failed (Result: exit-code) since 日 2020-06-28 15:31:55 CST; 6min ago
     Docs: http://docs.docker.com
  Process: 24481 ExecStart=/usr/bin/dockerd-current --add-runtime docker-runc=/usr/libexec/docker/docker-runc-current --default-runtime=docker-runc --exec-opt native.cgroupdriver=systemd --userland-proxy-path=/usr/libexec/docker/docker-proxy-current --init-path=/usr/libexec/docker/docker-init-current --seccomp-profile=/etc/docker/seccomp.json $OPTIONS $DOCKER_STORAGE_OPTIONS $DOCKER_NETWORK_OPTIONS $ADD_REGISTRY $BLOCK_REGISTRY $INSECURE_REGISTRY $REGISTRIES (code=exited, status=1/FAILURE)
 Main PID: 24481 (code=exited, status=1/FAILURE)

6月 28 15:31:54 iZ2ze67ifeuz62igol9apzZ systemd[1]: Starting Docker Application Container Engine...
6月 28 15:31:54 iZ2ze67ifeuz62igol9apzZ dockerd-current[24481]: time="2020-06-28T15:31:54.799852050+08:00" level=warning msg="could not change group /var/run/docker.sock to docker: group docker not found"
6月 28 15:31:54 iZ2ze67ifeuz62igol9apzZ dockerd-current[24481]: time="2020-06-28T15:31:54.800671443+08:00" level=info msg="libcontainerd: new containerd process, pid: 24490"
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ dockerd-current[24481]: time="2020-06-28T15:31:55.813485177+08:00" level=error msg="'overlay' not found as a supported filesystem on this host. Please ensure kernel is new enough and has overlay support loaded."
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ dockerd-current[24481]: time="2020-06-28T15:31:55.814654057+08:00" level=error msg="'overlay' not found as a supported filesystem on this host. Please ensure kernel is new enough and has overlay support loaded."
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ dockerd-current[24481]: Error starting daemon: error initializing graphdriver: devicemapper: Error running deviceCreate (CreatePool) dm_task_run failed
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ systemd[1]: docker.service: main process exited, code=exited, status=1/FAILURE
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ systemd[1]: Failed to start Docker Application Container Engine.
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ systemd[1]: Unit docker.service entered failed state.
6月 28 15:31:55 iZ2ze67ifeuz62igol9apzZ systemd[1]: docker.service failed.

```
解决方案如下
 卸载老版本的 docker 及其相关依赖
 

```bash
# 1、先查询所有安装的包

yum list installed | grep docker*
# 或者
rpm -qa docker*
# 2、删除查询出来的包

# 一般情况会有一个
yum remove -y docker-ce
# 18.09新增了cli工具
yum remove -y docker-ce-cli
# 3、删除镜像文件

rm -rf /var/lib/docker
rm -rf /var/lib/docker*
```

升级linux内核，重新安装docker：

```bash
#查看已经安装的和未安装的软件包组，来判断我们是否安装了相应的开发环境和开发库；
yum grouplist
#一般是安装这两个软件包组，这样做会确定你拥有编译时所需的一切工具
yum groupinstall "Development Tools"
#你必须这样才能让 make *config 这个指令正确地执行
yum install ncurses-devel
#如果你没有 X 环境，这一条可以不用
yum install qt-devel
#创建 CentOS-6 内核时需要它们
yum install hmaccalc zlib-devel binutils-devel elfutils-libelf-devel 
```

- 不好意思，上面的报错一直没有解决，找了许多方法去处理，但是始终是没有结果，于是我换了同事的服务器按照以上步骤安装。
- 下面的内容均基于CentOS Linux release 7.8.2003 (Core)

5.  查看安装版本,启动 docker

```bash
docker version
systemctl start docker
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630223714662.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630223733893.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
6. 验证是否安装成功

```bash
docker info
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630223820216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
7. 设置开机启动

```bash
 chkconfig docker on

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630224457370.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

## 配置Docker
1. 切换国内镜像源, 加速访问 Docker Hub

```bash
echo "OPTIONS='--registry-mirror=https://mirror.ccs.tencentyun.com'" >> /etc/sysconfig/docker
systemctl daemon-reload
service docker restart
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630224955549.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
2. 安装配置node环境

```bash
docker search node
docker pull docker.io/node:7.8.0

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630225022144.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630225130713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

3. 在自己喜欢的目录里创建Dockerfile文件

```bash
[root@VM_0_5_centos ~]# cd /var/opt/test
[root@VM_0_5_centos test]# ll
总用量 0
[root@VM_0_5_centos test]# touch Dockerfile

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630231730478.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630231906913.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

4. 假设Node.js应用的启动命令为node server.js, 监听端口为8090

```bash
# 可以指定依赖的node镜像的版本 node:<version>，如果不指定，就会是最新的
FROM node
WORKDIR /app

# 把其他源文件复制到工作目录
COPY ./app /app
# 把 package.json，package-lock.json(npm@5+) 或 yarn.lock 复制到工作目录(相对路径)
RUN npm install
# 只安装dependencies依赖
# 替换成应用实际的端口号
EXPOSE 8090
# 这里根据实际起动命令做修改
CMD [ "node", "server.js" ]


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705230429846.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
5. 补充.dockerignore

```bash
touch .dockerignore
```
.dockerignore内容如下

```bash
node_modules
npm-debug.log
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630233218185.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705232058192.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
6. 创建镜像

```bash
docker build -t node78:v1 .

```
在 Docker 守护进程执行 Dockerfile 中的指令前，首先会对 Dockerfile 进行语法检查，有语法错误时会返回：（如果按照上面的Dockerfile配置文件，不会报这个错，配置文件是后期修改过的，又重新截图的哦~）

```bash
[root@VM_0_5_centos test]# docker build -t node78:v1 .
Sending build context to Docker daemon 3.584 kB
Error response from daemon: Unknown instruction: ​：
```


7. 查看镜像

```bash
docker images
​
# 示例输出
REPOSITORY                      TAG        ID              CREATED
node                            8          1934b0b038d1    5 days ago
${your_name}/${image_name}    latest     d64d3505b0d2    1 minute ago
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020063023380787.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

8. 嘗試一下docker run node不僅可以可以尋找鏡像，如果沒有它就幫助你下載最新的版本
因为我下载的不是最新镜像，它自动开始搞最新啦

```bash
docker run node
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705173202831.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
9. 查看镜像
>你會看到我們有倆鏡像了,一個最新版,一個是初始下載的版本.要是不想要後期可以刪除哦~
>圖片裡的docker run 命令先不要執行哦~   
```bash
docker image ls
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705222720723.png)
 
10. 准备一个简单的nodejs文件

```bash
var http = require('http');

http.createServer(function (request, response) {


    response.writeHead(200, { 'Content-Type': 'text/plain' });


    response.end('Hello World\n');
}).listen(8090);

console.log('Server running at http://127.0.0.1:8090/');
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020070522593563.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705225247400.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705225633983.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

11. 构建镜像，不要忘了後面還有一個點點哦

```bash
docker build -t docker.io/node:latest .

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705230105411.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
 
* 启动容器脚本
```bash
docker run -d -p 8090:8090  docker.io/node:latest 

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705230144806.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
12. 测试，成功连接
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705232415710.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
 
 至此恭喜，部署成功！
 ## 常用命令
* 另外附一些常用命令：
```bash
# 查看所有容器(包括已终止的)
docker ps -a
# 或使用新命令
docker container ls -a
```

```bash
# 查看运行中的容器
docker ps
# 或使用新命令
docker container ls
​
# 示例输出
ID            IMAGE                                COMMAND    ...   PORTS
ecce33b30ebf  ${your_name}/${image_name}:latest  npm start  ...   49160->8080
```

```bash
# 查看某容器内日志
docker logs -f ${container_id}
```

```bash
# 进入某容器，并有shell执行环境
# 进入容器
# -i表示：交互式操作，-t表示：终端
docker exec -it ${container_id} bash
# 可通过输入 exit 退出 
```

```bash
# 停止容器
docker container stop ${container_id}
```

```bash
# 启动已终止的容器
docker container start ${container_id}
```

```bash
#删除容器
docker container rm ${container_name || container_id}

#查看镜像
docker images
# 或使用新命令
docker image ls

#删除镜像
docker image rm ${image_id}
```
## 结语:watermelon::watermelon::watermelon::watermelon::watermelon::watermelon:
> 本教程旨在快速完成Node.js项目部署，其他配置项詳細情況问题没有列举出来哦...后期有空会增加配置文章哟~~
> 欢迎大家指出文章需要改正之处&#x1F353;~  
> 如果有更好的方法，欢迎大家提出来，共同进步哟~~ 

