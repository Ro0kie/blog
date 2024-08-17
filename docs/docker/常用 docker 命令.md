---
hide:
  - toc        # Hide table of contents
---

```shell

#列出虚悬镜像
docker image ls -f dangling=true

#虚悬镜像已经失去了存在的价值，是可以随意删除的
docker image prune

#这个例子中演示了如何换行，
#对含有空格的值用双引号括起来
#这和 Shell 下的行为是一致的

ENV VERSION=1.0 DEBUG=on \
    NAME="Happy Feet"
```
