# Goal

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
- [用户信息](#用户信息)
	+ [id](#id)
	+ [who](#who)
	+ [whoami](#whoami)
	+ [users](#users)


- [系统上下文](#系统上下文)
	+ [uname](#uname)
	+ [hostname](#hostname)
	+ [uptime](#uptime)
	+ [date](#date)

	 
- []()	
	+ [](#)
	+ [](#)
	+ [](#)



- []()	
	+ [](#)



----

## <span id="用户信息">用户信息</span>

经常需要获取的用户信息：

- uid(用于判断是否为root用户) 'id -u'
- 用户的附属组(查看某个用户的所有组，判断该用户是否在组内) 'id -Gn'
- 当前init进程的运行级别 'who -r'
- 查看上次启动时间 'who -b'
- 查看当前登陆用户 'who'

Q1：有效(effective)用户和真实(real)用户的区别在哪？

#### <span id="id">id</span>

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




#### <span id="who">who</span>

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

#### <span id="whoami">whoami</span>

whoami 打印用户有效名称，与"id -un" 结果相同

#### <span id="users">users</span>

users 打印当前所有在线用户的用户名


## <span id="系统上下文">系统上下文</span>

经常需要获取的系统上下文信息：

- CPU架构(比如在下载的软件的时候需要确定是x86还是x86_64) 'uname -p'
- 查看系统名称 'uname -n'
- 操作系统发行版(是centos还是ubuntu)
- 查看或设置当前日期 '查看：date，'
- 

#### <span id="uname">uname</span>

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

#### <span id="hostname">hostname</span>

hostname 打印主机名称，与uname -i相同(最起码我没发现什么不一样的地方)

example:
```shell
[root@vultr ~]$ hostname
vultr.guest
```

#### <span id="uptime">uptime</span>

uptime 打印系统已正常运行的时间，

option:

+ -p/--pretty 更友好的格式打印

example：

```shell
[root@vultr ~]$ uptime
 当前时间 	 系统已正常运行时间  		当前登陆用户数		负载均衡(但我也搞不懂这个参数的含义)
 15:36:14 up 19 days, 16:24,  		2 users,  			load average: 0.00, 0.00, 0.00
```
#### <span id="date">date</span>


example：



## 待观察命令(因为我不知道这些命令暂时用在哪些地方,所以就暂时不整理)：

- nproc
- hostid

## <span id="用户信息">用户信息</span>

#### <span id="id">id</span>


[参考]()
