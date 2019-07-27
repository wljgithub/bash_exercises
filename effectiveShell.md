[TOC]

# 目的

受到陈皓前辈[这篇文章](https://coolshell.cn/articles/19219.html)的启发，打算搭建一个高效的Shell开发环境，并萌生了记录这个实现过程的念头。


## 命令行

### alias

```shell
alias nis="npm install --save "
alias svim='sudo vim'
alias mkcd='foo(){ mkdir -p "$1"; cd "$1" }; foo '
alias install='sudo apt get install'
alias update='sudo apt-get update; sudo apt-get upgrade'
alias ..="cd .."
alias ...="cd ..; cd .."
alias www='python -m SimpleHTTPServer 8000'
alias sock5='ssh -D 8080 -q -C -N -f user@your.server'
```

### 一键配置脚本