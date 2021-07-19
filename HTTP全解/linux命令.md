* mkdir 创建文件夹
* rmdir 删除文件夹

#### 编辑文件
* 

#### 快捷键
* ctrl + a : 快速回到命令前面
* ctrl + e : 快速回到命令最后
* sudo !! : sudo执行上一句命令

#### 设置密码
adduser XXX 未提示输入密码，或需要修改密码，root用户执行以下命令
```
passwd <username>
```
之后输入密码就可以啦！

#### git部署应用
```
git clone https://github.com/FrankFang/nodejs-test.git
cd nodejs-test
touch log
启动命令：node server.js 8888 > log 2>&1 &
把启动命令做成 start 文件
  touch start
  echo 'node server.js 8888 > log 2>&1 &' >> ./start
  cat start
添加执行权限 chmod +x ./start
运行 sh ./start 得到一个进程号 pid
tail log 看 log 内容
kill -9 pid 可以关掉进程
killall node 可以关掉所有 node 进程
```
