# Linux学习之路
将学过和要学习的Linux知识整理成一个体系

# Linux 常用命令

- [文件系统操作](#1)

- [指令与文件搜索 ](#1.1)

- [字符处理](#1.2)

- [权限管理](#1.3)

- [网络命令](#1.4)

- [进程监视](#1.5)



<h2 id="1">文件系统操作</h2>

显示当前目录

    $ pwd

切换目录

    $ cd <目录>

切换到上一级目录

    $ cd ..


    $ 



    $ 




<h2 id = "1.1">指令与文件搜索</h2>

#### 1.which
指令搜索
```bash
which [-a] command

-a : 将所有指令列出，而不只是第一个
```

#### 2. whereis
文件搜索，速度比较快，因为只搜索特定几个目录
```bash
whereis (选项) (参数)

选项
-b：执照二进制文件
-f：不现实文件名前的路径名


参数 
指令名：要查找的二进制程序、源文件和man手册页的指令名
```

示例1：找出
#### 3. locate
文件搜索，可以用关键字或者正则表达式来

locate 使用/var/lib/mlocate/ 这个数据库来进行搜索，他存储在内存中，并且每天更新一次，所以无法用locate搜索新疆的文件，可以使用updatedb来更新数据库

	locate [-ir] keyword
	-r :正则表达式

#### 4. find

文件搜索，可以使用文件的属性和权限进行搜索

```bash
find [basedir] [option]
example : find . -name "shadow"

```
(一)：与时间有关的选项：
```bash
-mtime n   ：列出 n天之前的那一天修改过内容的文件
-mtime +n  ：列出 n天之前（不含n天本身）修改过内容的文件
-mtime -n  ：列出在n天之内（含n天本身）修改过内容的文件
-newer file ：列出比file更新的文件
```
(二)与文件拥有者所属组有关的选项
```bash
-uid n
-gid n
-user name
-group name
-nouser :搜索拥有着不存在 /etc/passwd的文件
-nogroup：搜索所属组不存在于 /etc/group 的文件
```

(三)与文件权限和名称有关的选项
```bash
-name filename
-size [+-]SIZE: 搜寻比SIZE还要大（+）或小（-）的文件。这个SIZE的规格有：c：代表byte，k：代表 1024bytes。所以，要找比50KBh还要大的文件，就是 -size +50k
```

<h2 id="1.4">网络命令 </h2>

ping 主机测试连接状态
        
    $ ping <host> 


查看远程登陆的ip

    $ whois

下载文件

    $ curl -O <url/to/file>

 以host对username创建ssh连接

    $ ssh <username>@<host>

复制文件到远程主机

    $ scp <file>
    <user>@<host>:/remote/path

<h2 id = "1.5">进程监视</h2>

#### 1. ps

显示自己的进程

	 ps -l

查看系统所有进程

	ps aux

查看特定的进程

	ps aux |grep threadname

#### 2. top

 动态的显示当前运行的进程

    $ top

#### 3. kill
关闭某个进程

    $ kill <pid>

#### 4. pstree
查看进程树

	pstree -A




# Linux 概念及其相光命令

- [用户管理]()
- [文件权限]()
- [进程]()
- [包]()

	
# Shell 习题集

# 参考

- [Python-100-Days/Day31-35/玩转Linux操作系统](https://github.com/jackfrued/Python-100-Days/blob/master/Day31-35/%E7%8E%A9%E8%BD%ACLinux%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F.md)

- [Interview-Notebook/notes/Linux](https://github.com/CyC2018/Interview-Notebook/blob/master/notes/Linux.md#%E4%B8%80%E5%B8%B8%E7%94%A8%E6%93%8D%E4%BD%9C%E4%BB%A5%E5%8F%8A%E6%A6%82%E5%BF%B5)