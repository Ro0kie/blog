```shell
-A	指定客户端的用户代理标头,即 User-Agent
curl -A 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36' https://www.google.com
```



```shell
-b	向服务器发送 Cookie
curl -b 'foo1=bar;foo2=bar2' https://www.google.com
curl -b cookies.txt https://www.google.com
```



```shell
-X(大写)	指定 HTTP 请求的方法
curl -X POST https://www.example.com

-x(小写)	指定 HTTP 请求的代理
curl -x socks5://james:cats@myproxy.com:8080 https://www.example.com
```



```shell
-u	设置服务器认证的用户名和密码
curl -u 'bob:12345' https://google.com/login
```



```shell
-O	将服务器回应保存成文件，并将 URL 的最后部分当作文件名
curl -O https://www.example.com/foo/bar.html
```



```shell
--limit-rate	限制 HTTP 请求和回应的带宽，模拟慢网速的环境
curl --limit-rate 200k https://www.google.com
每秒200KB
```



```shell
-H	添加 HTTP 请求的标头
  curl -H 'Accept-Language: en-US' -H 'Secret-Message: xyzzy' https://google.com
```



```shell
-G	构造 URL 的查询字符串
curl -G -d 'q=kitties' -d 'count=20' https://google.com/search

上面命令会发出一个 GET 请求，实际请求的 URL 为
https://google.com/search?q=kitties&count=20 如果省略-G，会发出一个 POST 请求
```



```shell
-F	向服务器上传二进制文件

curl -F 'file=@photo.png' https://google.com/profile
上面命令会给 HTTP 请求加上标头Content-Type: multipart/form-data，然后将文件photo.png作为file字段上传

-F	可以指定 MIME 类型
curl -F 'file=@photo.png;type=image/png' https://google.com/profile

-F	也可以指定文件名
curl -F 'file=@photo.png;filename=me.png' https://google.com/profile

上面命令中，原始文件名为photo.png，但是服务器接收到的文件名为me.png。
```



```shell
-d	用于发送 POST 请求的数据体
curl -d'login=emma＆password=123'-X POST https://google.com/login
curl -d 'login=emma' -d 'password=123' -X POST  https://google.com/login

使用-d参数以后，HTTP 请求会自动加上标头Content-Type : application/x-www-form-urlencoded
并且会自动将请求转为 POST 方法，因此可以省略-X POST

-d	可以读取本地文本文件的数据，向服务器发送。
curl -d '@data.txt' https://google.com/login
```



```shell
-L	让 HTTP 请求跟随服务器的重定向     curl 默认不跟随重定向
curl -L -d 'tweet=hi' https://api.twitter.com/tweet
```



```shell
-s	不显示统计信息
curl -s ip.gs
```

