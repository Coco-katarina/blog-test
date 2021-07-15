# HTTP
## 基础概念
### 请求
请求动词(GET/POST/PUT/PATHC/DELETE) 路径加查询参数 协议名/版本   

* host: 域名或IP
* accept: text/html
* content-type: 请求体的格式

#### 细节
三部分：请求行、请求头、请求体

### 响应
协议名/版本 状态码 状态字符串
* content-type: 响应体的格式

#### 细节
三部分：状态行、响应头、响应体

## 用curl构造请求
curl -v http://127.0.0.1:8888
### 设置请求动词
* -X POST
* 注意大小写

### 设置路径和查询参数
* 直接在url后面加

### 设置请求头
* -H 'Name:Value'或者 --header'Name:Value'

### 设置请求体
* -d'内容'或者--data'内容'

## 读取请求（node.js）
### 读取请求动词
* request.method

### 读取路径
* request.url 路径，带查询参数
* path纯路径，不带查询参数
* query 只有查询参数

### 读取请求头
* request.headers['Accept']

## 设置响应（node.js）
### 设置响应状态码
* request.statusCode = 200

### 设置响应头
* response.setHeader('Content-Type','text/html');

### 设置响应体
* response.write('内容')
* 可持续追加内容
