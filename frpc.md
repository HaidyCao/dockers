# FRPC docker

## 准备文件

- frpc 可执行文件，找到对应系统和芯片架构的
- frpc.ini 配置文件
- Dockerfile
  ```
  FROM golang:latest
  
  COPY frp_0.57.0_linux_arm64/frpc /usr/local/bin/
  COPY frpc.ini /data/frpc.ini
  
  CMD ["/usr/local/bin/frpc", "-c", "/data/frpc.ini"]
  
  ```
  解释：FROM golang，这个是没必要的，本来只是为了直接从源码编译，其实没啥必要，大部分常用架构都可以在官方 release 页面下载得到。

## 创建镜像
执行命令 `docker build -t <image_name> .`

## 运行

执行命令 `docker run -d -p <host_port>:<container_port> --restart=always <image_name>`
- -d 后台运行
- -p 端口映射
- --restart=always 开机启动
