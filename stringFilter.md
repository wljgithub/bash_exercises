## awk

### 过滤记录

#### 运算符

逻辑运算符
\>,<,==,>=,<=,

条件运算符
&& ||

正则表达式

$2 ~ /pattern/

或匹配

$2 ~ /pattern1|pattern2/

模式取反

$2 !~ /pattern/


awk当grep用： awk '/pattern/' filename

### 文件拆分

awk 'NR!=1{print > $6}'

if-else

awk 'NR!=1{if ($6 ~ // )print >"1.txt";else if ($6 ~ //) print >"2.txt";else print >"3.txt"}' ss.txt

### 统计

统计目录中xx文件的大小

ls -l \*.cpp \*.h \*.c |awk {sum+=$5} END {print sum} 

通过数组的方式统计各类连接数

awk 'NR!=1{a[$6]++;} END {for (i in a) print i ", " a[i];}' netstat.txt


99乘法表，好帅。
```
seq 9 | sed 'H;g' | awk -v RS='' '{for(i=1;i<=NF;i++)printf("%dx%d=%d%s", i, NR, i*NR, i==NR?"\n":"\t")}'
```


