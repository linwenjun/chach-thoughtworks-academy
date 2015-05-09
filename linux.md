## linux 文件结构


### 查看distribution和linux标准

```
uname -r ##查看实际内核版本
lsb_release -a ##查看发行版本
```



### FHS (FileSystem Hierarchy Standard)

||shareable|unshareable|
|-----|-----|-----|
|static|/usr(软件放置处)|/etc(配置处)|
||/opt(第三方软件)|/boot(开机与内核文件)
|variable|/var/mail|/var/run
||/var/spool/news|/var/lock



### 常见目录(FHS)
|目录|说明|
|---|---|
|/|所有目录的根，与开机，还原，系统修复有关，**根目录应该越小越好**|
|/usr|与软件安装、执行有关，|
|/var|与系统运作过程有关|
|/bin|放置但用户维护模式下还能够操作的命令|
|/boot|开机会用到的文件
|/dev|设备与接口设备|



### 常见目录(FHS)续
|目录|说明|
|---|---|
|**/etc**|系统主要的配置文件
|**/home**|用户主文件夹
|/lib|函数库，在开机时会用到
|/media|挂载的设备
|/mnt|挂载的额外的设备，
|/root|系统管理员的主文件夹



### 常见目录(FHS)续
|目录|说明|
|---|---|
|/sbin|root能够用来设置系统的命令
|/srv|一些网络服务启动后，这些服务所需要的数据目录
|/tmp|临时文件夹，任何人都可以访问，不建议放置重要数据



### 常见目录(非FHS)
|目录|说明|
|---|---|
|/lost+found|使用标准的ext2/ext3文件系统格式才会产生的一个目录|
|/proc|虚拟文件系统，放置内存当中各种内核，进程，外部设备的状态及网络|
|/sys|这个目录其实跟/proc非常像，目前已加载的内核模块等，同样不占用内盘容量




## linux 文件权限



|代表字符 |权限|对文件和含义|对目录的含义 | 代表数字 |
|------- |---|---       |---        | ----    |
|r       |读  | 查看文件内容 | 列出目录中的内容 | 4
|w       |写  | 修改文件内容 | 在目录中创建，删除文件 | 2 |
|x       |执行| **可以执行文件**  | 可以进入目录 | 1 |



### 用户类别 user group other root



### 相关命令
```
chmod [who] operator [permission] filename
```
#### who: u g o a
#### operator + - =
#### permission r w x



### 例子 #增加当前用户对demo的执行权限
```
chmod u+x demo
```



### 作业：用chomd命令证明目录和文件的权限
```
#tips 写文件
echo "abc" > demo
echo "abc" >> demo
```



### 关于文件可执行的例子 shell script
```
创建 first.sh
```

```
#!/bin/sh
#对变量赋值：
hello_world="hello world"
# 现在打印变量的内容：
echo $hello_world
```



### 关于 $PATH
```
expert PATH=$PATH:/path
```