---
hide:
  - toc        # Hide table of contents
---


```shell
#换源

FROM alpine
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

FROM ubuntu
RUN  sed -i s@/security.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list\
    &&sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list

#列出虚悬镜像
docker image ls -f dangling=true

#虚悬镜像已经失去了存在的价值，是可以随意删除的
docker image prune

#这个例子中演示了如何换行，以及对含有空格的值用双引号括起来的办法，这和 Shell 下的行为是一致的
ENV VERSION=1.0 DEBUG=on \
    NAME="Happy Feet"
```
