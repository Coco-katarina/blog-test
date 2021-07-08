# URL  - Uniform Resource Locator 统一资源定位符  
## 组成   
协议 + 域名或IP + 端口号 + 路径 + 查询字符串 + 锚点

### 端口  
* HTTP：80
* HTTPS；443
* FTP :21   

一共有65535个端口，0到1023号端口留给系统使用的（管理员权限），其他端口给普通用户使用

### IP
域名就是对IP的别称  
#### 知识点
* 一个域名可以对应不同IP，均衡负载 
* 一个IP可以对应不同域名

### curl命令 
* 用curl可以发HTTP请求
 `curl -v https://baidu.com`
 
 `curl -s -v -- https://www.baidu.com`
 * 理解以下概念
 1. url会被curl工具重写，先请求DNS(Domain Name System域名系统)获得IP
 2. 先进行TCP连接，TCP连接成功后，开始发送HTTP请求
 3. 请求内容看一眼
 4. 响应内容看一眼
 5. 响应结束后，关闭TCP连接（看不出来）
 6. 真正结束

### HTTP - HyperText Transfer Protocol超文本传输协议
