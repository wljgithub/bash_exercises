[TOC]

## Wget 

### 概述

GNU Wget是一个可以从网站中下载文件的工具，支持 HTTP，HTTPS，FTP，和HTTP代理

- non-interactive,download file without user's presence(非交互式)
- recursive download whole web sites(可以递归下载整个网站) 
- support file name wildcard when retrieving via FTP;read timestamp given by http and ftp servers,save it locally,thus it can retrieving the new version if the servers has(支持FTP文件通配符下载，指定时间下载最新的版本？)
- designed for unstable network connection,while download fails due to network,it will keep retrieving until whole file has been retrived.(下载失败，重新下载)
- support proxy(支持代理)
- support ipv6(支持ipv6)
- offer mechanisms to follow the link you wish(支持重定向)
- the progress of non-interative download is traced as dot,ohters is traced as thermometer style.(下载状态显示)
- most of feature are fully configurable,either through command line option or initialization file(global startup files /usr/local/etc/wgetrc),and can specific startup file via command line option.(支持配置)


[GNU文档参考](https://www.gnu.org/software/wget/manual/wget.html)


## yum

[ Red Hat Customer Portal](https://access.redhat.com/solutions/9934)