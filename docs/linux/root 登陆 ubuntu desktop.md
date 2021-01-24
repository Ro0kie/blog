---
hide:
  - toc        # Hide table of contents
---

ubuntu desktop 用非 root 用户登陆的时候，小问题很多

尤其是anaconda , 没法隔离环境，创建出一个环境test，结果conda install 还是装在base里面



干脆就root登陆吧  不得不说，root登陆也有问题。。。。tmd真的烦



```shell
vim /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
在文档末尾输入
greeter-show-manual-login = true
all-guest = false

vim /etc/pam.d/gdm-autologin 
释掉以下语句
auth required pam_succeed_if.so user != root quiet_success

vim  /etc/pam.d/gdm-password
释掉以下语句
auth required pam_succeed_if.so user != root quiet_success

vim /root/.profile
文档最后一行 mesg n || true 前添加 tty -s && 即 tty -s &&mesg n || true

reboot
```



#### root登陆的问题

chrome 会因为root登陆出问题

```shell
vim /usr/share/applications/google-chrome.desktop 

Exec=/usr/bin/google-chrome-stable %U
后面加上  --no-sandbox
```