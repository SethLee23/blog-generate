---
title: HTTP请求与响应
date: 2019-03-01 20:51:48
tags:
---
# 一、关于HTTP请求与响应
## * HTTP请求内容
* 1 动词 路径 协议/版本
* 2 Key1: value1
* 2 Key2: value2
* 2 Key3: value3
* 2 Content-Type: application/x-www-form-urlencoded
* 2 Host: www.baidu.com
* 2 User-Agent: curl/7.54.0
* 3 
* 4 要上传的数据

解释：请求最多包含四部份，第一部分为：“动词 路径 协议、版本”，第二部分为：“key:value”，第三部分永远是回车，第四部分如果有，就表示要上传的数据。
##### *注：动词有：GET POST PUT PATCH DELETE HEAD OPTIONS
## * HTTP响应内容
* 1 协议/版本号 状态码 状态解释
* 2 Key1: value1
* 2 Key2: value2
* 2 Content-Length: 17931
* 2 Content-Type: text/html
* 3
* 4 要下载的内容

解释：响应包含四部分，第一部分为：“协议/版本号 状态码 状态解释”，第二部分为：“key:value”，其中Content-Type标注了第四部分的格式，第三部分为回车，第四部分表示要下载的内容。
## * 使用Chrome开发者工具查看HTTP请求与响应内容
1.进入网页后右键选择“检查”，进入页面，选择"Network"，选中"Hide data URLs"，
2.输入网址，选中第一个响应
查看 Request Headers/Response Headers，点击「view source」，
你会看到响应的前两部份，示意图如下
![chrome.png](https://i.loli.net/2019/03/01/5c7933c9a3321.png)
![chrome2.png](https://i.loli.net/2019/03/01/5c793773018d9.png)
3.如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到，查看 Response 或者 Preview，你会看到响应的第 4 部分。
# 二、如何使用curl命令
 常见的curl命令：

1.curl -I选项，(HTTP)只输出HTTP-header，不获取内容(HTTP/FTP/FILE)。
用于HTTP服务时，获取页面的http头；
  （如：curl -I http://baidu.com）
用于FTP/FILE时，将会获取文件大小、最后修改时间
  （如：curl -I file://test.txt）

2.curl -A,设置Http请求头“User-Agent”，服务器通过“User-Agent”可以判断客户端使用的浏览器名称和操作系统类型，伪造此参数能导致服务器做出错误判断,设置用户代理就可以伪装客户端身份（如：curl -A testagent http://www.yinzhengjie.org.cn）

3.curl -e，设置访问时的来源页面，告诉http服务从哪个页面进入到此页面（如：curl -e http://www.google.com/index.html http://www.baidu.com）

4.-cacert，指定CA证书 (SSL)(如：curl --cacert /etc/pki/CA/cacert.pem https://www.yinzhengjie.org.cn）

5.访问网页（如curl www.baidu.com）

6.curl -i,显示http response的头信息(如：curl -i www.baidu.com)

7.curl -v,显示一次http请求与响应的过程（如：curl -v www.baidu.com）

8.Curl执行GET/POST/PUT/DELETE操作（如：curl -X GET www.baidu.com）

9.查看帮助：curl --help









博客参考自：<http://aiezu.com/article/linux_curl_command.html>
<https://www.cnblogs.com/yinzhengjie/p/7719804.html>