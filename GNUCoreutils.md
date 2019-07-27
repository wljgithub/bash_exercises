[TOC]

# 目的

- 之所以想整理[GNUCoreutils](https://www.gnu.org/software/coreutils/manual/html_node/index.html)的目的在于希望在脑海里构建一个linux工具体系，当建立起工具体系的概念后，以后对linux中的各种命令的使用就不会这么混乱了，否则学习再久，如果知识不成体系，也都只是在强行的背那个命令而已，没太大的意义。

- 同时这也希望它变成我所学过的linux命令的汇总 (因为我是个健忘的人，经常忘记自己学过什么)，并在整理的时候尽可能地保持文档的简洁，以便以后忘了方便查询

 
# 目录


```
下载
wget
curl
yum

条件判断
算术运算

格式化输出，颜色

echo 1 > /proc/sys/net/ipv4/ip_forward 

firewalld
systemctl
```
硬骨头
```
iptables
ip

```

## 截取文件文本(Ouput of parts of files)

### head

head 默认输出文件的前十行，如果未给定参数或给定-符号，则从标准输入读取

```shell
head [option]… [file]…
```
如果给定多个文件，则会在打印每个文件的头部，以便区分

option：

+ -c [-]num /--bytes=[-]num 打印前xx字节，如果num前带"-"号则打印除了倒数第xx字节以外的所有内容，也可以打印KB或MB等，如下：
```
‘b’  =>            512 ("blocks")
‘KB’ =>           1000 (KiloBytes)
‘K’  =>           1024 (KibiBytes)
‘MB’ =>      1000*1000 (MegaBytes)
‘M’  =>      1024*1024 (MebiBytes)
‘GB’ => 1000*1000*1000 (GigaBytes)
‘G’  => 1024*1024*1024 (GibiBytes)
```
当然，还有更打的 ‘T’, ‘P’, ‘E’, ‘Z容量也是支持的
+ -n [-]num/ --lines=[-]num 打印前xx行，带"-"号则打印前xx行以为的所有内容
+ -q /--quiet/--silent 不打印文件头部(多个文件的时候会用到)

### tail

tail 默认打印文件末尾的10行文本，如果未给定参数或给定-符号，则从标准输入读取

```shell
tail [option]… [file]…
```

option：
+ -c[+]num/--bytes=[+]num 末尾xx字节，带＋号则是除了头xx字节外的所有字节,与head一样tail也支持其他换算单位，如下：

```shell
‘b’  =>            512 ("blocks")
‘KB’ =>           1000 (KiloBytes)
‘K’  =>           1024 (KibiBytes)
‘MB’ =>      1000*1000 (MegaBytes)
‘M’  =>      1024*1024 (MebiBytes)
‘GB’ => 1000*1000*1000 (GigaBytes)
‘G’  => 1024*1024*1024 (GibiBytes)
```
+ -f

## Summarizing files(直译过来好怪)

### md5sum

md5sum 为每个文件计算128位的校验和


## 重定向

### tee


## 文件名操作(manipulation)

### pathchk

pathchk 检查文件名的有效性和便携性(portablility)

```shell
pathchk [option]… name…
```
如果参数满足以下条件则会打印错误信息：

- 文件名为空
- 文件所在目录无执行权限
- 文件名超出操作系统所支持最大长度
- 文件名的其中一个部分(component of name)超出文件系统最大值 

文件名不存在不是一个错误

option：

+ -p 如果满足以下条件，打印错误信息
	* 文件名为空
	* 文件名不满足POSIX文件名字符集(字母，数字，".","\_", "-", "/")
	* 文件名超出POSIX最小限制(我也不知道多小)

+ -P 如果文件名为空或文件名的其中一部分以"-"开始，打印错误信息


### basename

basename 可用于删除文件名的目录和后缀部分

```shell
basename name [suffix]
basename option… name…
```
option：

+ -a/--mutiple 支持多个过滤多个文件名，使用该选项需要搭配-s指定后缀
+ -s suffix/--suffix=suffix 删除文件后缀
+ -z/--zero 以0byte结尾（ASCLL NUL），默认是换行符，我也不知道有什么用

example：
```shell
# Output "sort".
basename /usr/bin/sort

# Output "stdio".
basename include/stdio.h .h

# Output "stdio".
basename -s .h include/stdio.h

# Output "stdio" followed by "stdlib"
basename -a -s .h include/stdio.h include/stdlib.h
```
### dirname

dirname 从名字上看就知道是只取目录名（会删除最后一个斜杠，如果有的话）

```shell
dirname [option] name…
```

example：

```shell
# Output "/usr/bin".
dirname /usr/bin/sort
dirname /usr/bin//.//

# Output "dir1" followed by "dir2"
dirname dir1/str dir2/str

# Output ".".
dirname stdio.h
```

## 工作环境上下文(Working context)

### pwd

pwd 输出当前目录

option：

+ -L/--logical 如果目录有软连接，输出软链接
+ -P/--physical 输出目录真实路径

如果-L和-P都给了，取最后那个，不填则默认-P

> 考虑到shell alias或内置pwd函数的影响，推荐使用 env pwd避免输出非预期的结果

### tty

tty 打印连接标准输入的终端的文件名，如果标准输入不是一个终端，打印"not a tty"

option：

+ -s
+ slient
+ quiet

以上选项只有退出状态

- 0：标准输入是一个终端
- 1：标准输入是一个非终端文件
- 2：给定参数错误
- 3：出现错误

### stty

stty打印或改变终端特性，如波特率(baud rate)

这个暂时不整理，需要用到再整理

## 用户信息

经常需要获取的用户信息：

- uid(用于判断是否为root用户) 'id -u'
- 用户的附属组(查看某个用户的所有组，判断该用户是否在组内) 'id -Gn'
- 当前init进程的运行级别 'who -r'
- 查看上次启动时间 'who -b'
- 查看当前登陆用户 'who'

Q1：有效(effective)用户和真实(real)用户的区别在哪？

### id

id 打印与用户有关的信息，未指定用户则打印自身信息(包含uid,gid,groups)

	id [option]… [user]…

option

+ -g/--group  	只打印组ID
+ -G/groups		打印组及其附属组ID
+ -u/--user		只打印UID
+ -n/--name 	打印用户名而不是ID数字，需要搭配-u,-g,-G使用

example:
```shell
# 输出当前用户真实ID
id -ru

# 输出当前用户的所有组名(与groups命令结果相同)
id -Gu

#
```
[参考](https://www.gnu.org/software/coreutils/manual/html_node/id-invocation.html#id-invocation)




### who

who 打印当前正在登陆的用户

	who [option] [file] [am i]

option:

+ -a/--all 与-b -d --login -p -r -t -T -u相同
+ -b/--boot 打印上次启动的日期和时间
+ -r/--runlevel 打印当前init进程的运行级别

example:
```shell
[root@vultr ~]$ who
# 用户名	 terminal line  login time 				remote hostsname or X display
root     pts/0          2019-07-23 10:26 			(153.44.193.213)
```

### whoami

whoami 打印用户有效名称，与"id -un" 结果相同

### users

users 打印当前所有在线用户的用户名


## 系统上下文

经常需要获取的系统上下文信息：

- CPU架构(比如在下载的软件的时候需要确定是x86还是x86_64) 'uname -p'
- 查看系统名称 'uname -n'
- 操作系统发行版(是centos还是ubuntu)
- 查看或设置当前日期 '查看：date，'
- 

### uname

uname 打印操作系统和硬件相关的信息，不填选项默认 -s

	uname [option]…

option:

+ -a/--all 所有信息(忽略未知的硬件平台和CPU类型)
+ -m/--machine 硬件信息(CPU架构)
+ -n/--nodename 网络节点主机名
+ -o/--operating-system 操作系统名
+ -r/--kernel-realse 内核发行版

example：
```shell
[root@vultr ~]$ uname -a
Linux vultr.guest 5.1.15-1.el7.elrepo.x86_64 #1 SMP Tue Jun 25 10:52:45 EDT 2019 x86_64 x86_64 x86_64 GNU/Linux
```

### hostname

hostname 打印主机名称，与uname -i相同(最起码我没发现什么不一样的地方)

example:
```shell
[root@vultr ~]$ hostname
vultr.guest
```

### uptime

uptime 打印系统已正常运行的时间，

option:

+ -p/--pretty 更友好的格式打印

example：

```shell
[root@vultr ~]$ uptime
 当前时间 	 系统已正常运行时间  		当前登陆用户数		负载均衡(但我也搞不懂这个参数的含义)
 15:36:14 up 19 days, 16:24,  		2 users,  			load average: 0.00, 0.00, 0.00
```
### date


example：



## 待观察命令

因为我不知道这些命令暂时用在哪些地方,所以就暂时不整理

- nproc
- hostid
- printenv (这个命令怎么感觉有点多余？echo $HOME不是可以实现同样的效果么?)
