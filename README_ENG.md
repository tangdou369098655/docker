@[Use Docker to create a Node Development Environment Based on CentOS Linux release 7.8.2003 Core](https://github.com/tangdou369098655/docker/edit/master/README.md)


English | [简体中文](https://github.com/tangdou369098655/docker/blob/master/README.md)

## Introduction
* This article describes how to deploy and use docker in CentOS Linux release 7.8.2003
* The purpose is to use the simplest and fastest way to solve the deployment requirements of Nodejs using Docker



## Precondition
>You need a server~~
>Open it, just like this on below


![在这里插入图片描述](https://img-blog.csdnimg.cn/2020052418024250.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
## Remarks
- Because the alicloud server was originally used for the installation, the ECS instance of aliyun Linux 2.1903 LTS 64 bit operating system encountered some problems in the later stage. After querying a lot of data and operating according to the data, but the problem has not been solved for the time being, so I used my colleague's server to install it again.
- The specific configuration is as follows
- View Linux Kernel


```bash
uname -a
cat /proc/version
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630222141221.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

- View the details of the current system version

```bash
1.cat /etc/redhat-release(This method is only suitable for RedHat Linux)
2.lsb_release -a (This command applies to all Linux distributions）
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630222951679.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

## Step 1: Link server
1. After the link is successful, it is shown in the figure below. If you don't know how to link, you can refer to (this address)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200524181539512.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
2. Run the following commands in turn to add the yum source.

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

3. Install and run Docker。

```bash
yum install docker-io -y
systemctl start docker
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153130693.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153143730.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200628153644197.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)


4. Solve the error report and check the error information: (Note: if you use CentOS Linux, you can skip this step directly, generally there is no problem below)
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

 The solution is as follows 
 Uninstall the old version of docker and its related dependencies 

```bash
# 1、Query all installed packages first

yum list installed | grep docker*
# Perhaps
rpm -qa docker*
# 2、Delete the query package

# Generally, there will be one
yum remove -y docker-ce
# Added cli tool
yum remove -y docker-ce-cli
# 3、Delete image file

rm -rf /var/lib/docker
rm -rf /var/lib/docker*
```

Upgrade the Linux kernel and re install docker：

```bash
#Check the installed and non installed packages to detemine whether we have installed the corresponding development environment and development library
yum grouplist

#This is usually done by installing both packages, which will make sure you have all the tools you need to compile
yum groupinstall "Development Tools"
#You have to do this to get the make * config command to execute correctly.
yum install ncurses-devel
#If you don't have this environment, you can use this one.
yum install qt-devel
#They are required to create the CentOS-7 Kernel.
yum install hmaccalc zlib-devel binutils-devel elfutils-libelf-devel 
```


- Sorry, the above error has not been solved, and many methods have been found to deal with it, but there is no result. So I changed my colleague's server and installed it according to the above steps.
- The following is based on CentOS Linux release 7.8.2003 (Core)

5.  Check the installation version and start docker.

```bash
docker version
systemctl start docker
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630223714662.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630223733893.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
6. Verify that the installation was successful

```bash
docker info
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630223820216.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
7. Set boot up

```bash
 chkconfig docker on

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630224457370.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

## Configure Docker
1. Switch domestic image source to accelerate access to Docker Hub

```bash
echo "OPTIONS='--registry-mirror=https://mirror.ccs.tencentyun.com'" >> /etc/sysconfig/docker
systemctl daemon-reload
service docker restart
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630224955549.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
2. Install and configure node environment.

```bash
docker search node
docker pull docker.io/node:7.8.0

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630225022144.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630225130713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

3. Create a dockerfile file in your favorite directory.

```bash
[root@VM_0_5_centos ~]# cd /var/opt/test
[root@VM_0_5_centos test]# ll
总用量 0
[root@VM_0_5_centos test]# touch Dockerfile

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630231730478.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630231906913.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

4. Hypothesis Node.js The start command of the application is node server.js, The listening port is 8090

```bash
# You can specify the version of the dependent node image  node:<version>, if not specified, it will be the latest.
FROM node
WORKDIR /app

# Copy other source files to the working directory
COPY ./app /app
# Put package.json，package-lock.json(npm@5+) Or yarn.lock Copy to working directory(relstive path)
RUN npm install
# Install dependencies only
# Replace with the actual port number of the application 
EXPOSE 8090
# It is modified according to the actual start command
CMD [ "node", "server.js" ]


```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705230429846.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
5. Supplement .dockerignore

```bash
touch .dockerignore
```
.dockerignore  reads as follows

```bash
node_modules
npm-debug.log
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200630233218185.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705232058192.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
6. Create mirror

```bash
docker build -t node78:v1 .

```
Before the Docker deamons execute the instructions in the Dockerfile ，it will first check the syntax of the dockerfile. If there is a syntax error, it will be returned: (if you follow the above dockerfile cofiguration file, this error will not be reported. The configuration file has been modified later, and the screenshot is taker again.)

```bash
[root@VM_0_5_centos test]# docker build -t node78:v1 .
Sending build context to Docker daemon 3.584 kB
Error response from daemon: Unknown instruction: ​：
```


7. View image

```bash
docker images
​
# Sample output
REPOSITORY                      TAG        ID              CREATED
node                            8          1934b0b038d1    5 days ago
${your_name}/${image_name}    latest     d64d3505b0d2    1 minute ago
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020063023380787.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)

8. Try 'docker run node', which can not only find images, but also help you download the latest version if there is no node image.
Because I don't download the latest image, it will automatically start to download the latest version.

```bash
docker run node
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705173202831.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
9. View image
>You will see that we have two images, one is the latest version and the other is the original download version. If you don't want to delete it later~
>Do not execute the docker run command in the picture~
```bash
docker image ls
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705222720723.png)
 
10. Prepare a simple nodejs file
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

11. Build the image, don't forget there is a little bit behind it.

```bash
docker build -t docker.io/node:latest .

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705230105411.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
 
* Start container script
```bash
docker run -d -p 8090:8090  docker.io/node:latest 

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705230144806.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
12.Test, successful connected
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200705232415710.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3Rhbmdkb3UzNjkwOTg2NTU=,size_16,color_FFFFFF,t_70)
 
 Congratulations on the successful depluyment!
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
## 结语
> 本教程旨在快速完成Node.js项目部署，其他配置项詳細情況问题没有列举出来哦...后期有空会增加配置文章哟~~
> 欢迎大家指出文章需要改正之处~  
> 如果有更好的方法，欢迎大家提出来，共同进步哟~~ 

