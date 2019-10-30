# Docker-hello-world

最小的Docker镜像hello world生成示例(开发环境Amaze Linux)，生成的hello world Docker镜像仅910字节。

## 文件列表：
* hello.asm, hello的汇编源代码
* Makefile, asm程序的生成配置文件
* hello, 生成的二进制执行文件
* Dockerfile, 生成docker镜像描述文件
* README.md, 本文件

## 生成过程：

1. 安装Docker

 参考：在 Amazon Linux 实例上安装 Docker(https://www.jianshu.com/p/691f9e0e0f1b)
 
2. 安装Nasm编译环境

  sudo yum install -y nasm
  
3. 生成hello执行文件

  nasm hello.asm
  
4. 加入执行权限

  chmod +x ./hello
  
5. 生成镜像

  docker image build -t hello-world .

  docker images 

6. 运行镜像

  docker run -it hello-world

  结果如下：
```
Hello from Docker.
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (Assuming it was not already locally available.)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

For more examples and ideas, visit:
 http://docs.docker.com/userguide/

```  
Dockerfile内容：
```
FROM scratch
ADD hello /
CMD ["/hello"]

```


