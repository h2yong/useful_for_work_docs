<!--
 * @Author: h2yong@outlook.com
 * @Date: 2020-03-04 11:20:20
 * @LastEditTime: 2020-10-16 15:25:48
 * @LastEditors: Please set LastEditors
 * @Description: shell好命令
 -->

# shell 好命令
## 提取两个文件相同的内容

```bash
awk '{if(NR==FNR){a[$1]++};if(NR>FNR){for(i in a){if(i==$1) print $0}}}' a.txt b.txt > tmp.txt

comm -12 a.txt b.txt
```

## 查看 tcp 连接数状态的小脚本

```bash
netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
```

返回结果如下：  
　　 LAST_ACK 5  
　　 SYN_RECV 30  
　　 ESTABLISHED 1597  
　　 FIN_WAIT1 51  
　　 FIN_WAIT2 504  
　　 TIME_WAIT 1057  

tcp 连接状态：  
     CLOSED：无连接是活动的或正在进行  
　　 LISTEN：服务器在等待进入呼叫  
　　 SYN_RECV：一个连接请求已经到达，等待确认  
　　 SYN_SENT：应用已经开始，打开一个连接  
　　 ESTABLISHED：正常数据传输状态  
　　 FIN_WAIT1：应用说它已经完成  
　　 FIN_WAIT2：另一边已同意释放  
　　 ITMED_WAIT：等待所有分组死掉  
　　 CLOSING：两边同时尝试关闭  
　　 TIME_WAIT：另一边已初始化一个释放  
　　 LAST_ACK：等待所有分组死掉  

## 根据端口号杀死进程
```bash
kill `netstat -nlp | grep :8989 | awk '{print $7}' | awk -F"/" '{ print $1 }'`
```

## 输出超过指定大小的文件
```bash
find ~ -type f -size +500M
```

## 统计某列的数据之和
```bash
awk -F',' 'BEGIN{sum=0}{sum+=$2}END{print sum}' xx.txt
```

## 同时匹配多个字符
```bash
sed -n '/kobe/{/james/p}'
awk '/kobe/&&/james/{ print $0 }'
grep -E '(kobe.*james|james.*kobe)'    egrep  '(kobe.*james|james.*kobe)'
```

## 批量修改文件名
```bash
rename -v 's/14/04/' *.txt
```

## 查看磁盘使用率
```bash
$ iostat -d -x 1
Linux 3.0.101-0.47.55-default (host-10-22-0-88)         05/19/20        _x86_64_

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
xvda              0.01     2.40    0.04    0.97     2.32    26.91    29.01     0.01    6.26   0.91   0.09
xvdb              0.35    31.36    1.57    8.04    85.75   526.82    63.76     0.11   11.48   0.42   0.41
xvdc              0.53    13.56    6.18    3.03   265.16   207.67    51.37     0.08    8.39   0.56   0.51
xvdd              0.21     4.93    3.96    1.09   151.96    66.00    43.17     0.03    6.48   0.79   0.40
xvde              0.17     1.27    1.73    0.39    59.66    20.05    37.65     0.01    6.96   1.25   0.26
dm-0              0.00     0.00   14.69   63.67   562.54   820.54    17.65     0.17    2.21   0.19   1.46
```

## 查看监听端口被哪个进程占用

```bash
lsof -i:8080
```

```bash
$ netstat -pan | grep 3306
tcp        0      0 :::3306                 :::*                    LISTEN      126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:60102       ESTABLISHED 126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:11862       ESTABLISHED 126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:11858       ESTABLISHED 126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:11686       ESTABLISHED 126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:11856       ESTABLISHED 126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:11860       ESTABLISHED 126421/mysqld
tcp        0      0 10.22.0.88:3306         10.31.3.166:11894       ESTABLISHED 126421/mysqld
```

## 查看进程打开哪些文件

```bash
$ lsof -p 126421
COMMAND    PID  USER   FD   TYPE             DEVICE     SIZE/OFF      NODE NAME
mysqld  126421 mysql  rtd    DIR              202,2         4096         2 /
mysqld  126421 mysql  txt    REG              202,2     75004641    628702 /usr/sbin/mysqld
mysqld  126421 mysql  mem    REG              202,2       217016    852807 /var/run/nscd/group
mysqld  126421 mysql  mem    REG              202,2       217016    852806 /var/run/nscd/passwd
```

## 查看远程已打开的网络连接

```bash
$ lsof -i @10.31.3.166
COMMAND    PID  USER   FD   TYPE    DEVICE SIZE/OFF NODE NAME
mysqld  126421 mysql   49u  IPv6 469590066      0t0  TCP 10.22.0.88:mysql->10.31.3.166:13256 (ESTABLISHED)
mysqld  126421 mysql   56u  IPv6 470053702      0t0  TCP 10.22.0.88:mysql->10.31.3.166:11526 (ESTABLISHED)
mysqld  126421 mysql   61u  IPv6 470056476      0t0  TCP 10.22.0.88:mysql->10.31.3.166:11686 (ESTABLISHED)
mysqld  126421 mysql   65u  IPv6 470056477      0t0  TCP 10.22.0.88:mysql->10.31.3.166:11692 (ESTABLISHED)
mysqld  126421 mysql   67u  IPv6 469668577      0t0  TCP 10.22.0.88:mysql->10.31.3.166:56420 (ESTABLISHED)
mysqld  126421 mysql   69u  IPv6 470115277      0t0  TCP 10.22.0.88:mysql->10.31.3.166:27658 (ESTABLISHED)
mysqld  126421 mysql   79u  IPv6 469590073      0t0  TCP 10.22.0.88:mysql->10.31.3.166:13336 (ESTABLISHED)
mysqld  126421 mysql   80u  IPv6 470155006      0t0  TCP 10.22.0.88:mysql->10.31.3.166:40474 (ESTABLISHED)
mysqld  126421 mysql   81u  IPv6 469836899      0t0  TCP 10.22.0.88:mysql->10.31.3.166:64112 (ESTABLISHED)
mysqld  126421 mysql  153u  IPv6 469837031      0t0  TCP 10.22.0.88:mysql->10.31.3.166:64582 (ESTABLISHED)
```

## 查看占用空间较多的文件或目录

```bash
$ du -s /home/h2yong/logs/* | sort -n 
4	/home/h2yong/logs/app/olc
12	/home/h2yong/logs/tomcat
282140	/home/h2yong/easyconf
3122952	/home/h2yong/logs/app/run
15344724	/opt/huawei/logs/app/error

# 下面会多一行汇总
$ du -d 1 /home/h2yong/logs/* | sort -n 
4	/home/h2yong/logs/app/olc
12	/home/h2yong/logs/tomcat
282140	/home/h2yong/easyconf
3122952	/home/h2yong/logs/app/run
15344724	/opt/huawei/logs/app/error
18467696	/opt/huawei/logs
```

## 如何查看端口被哪个进程占用

```bash
# 方法一
lsof -i:端口号

# 方法二
netstat -tunlp|grep 端口号
```

# linux 命令大全

[man.linuxde.net](https://man.linuxde.net/par/3)
