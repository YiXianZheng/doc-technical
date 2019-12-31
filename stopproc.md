## 根据进程名称杀掉进程 stopproc.sh
#!/bin/sh
#根据进程名杀死进程
if [ $# -lt 1 ]
then
  echo "缺少参数：进程名称"
  exit 1
fi
 
PROCESS=`ps -ef|grep $1|grep -v grep|grep -v PPID|awk '{ print $2}'`
for i in $PROCESS
do
  echo "Kill the $1 process [ $i ]"
  kill -9 $i
done

## 执行./stopproc.sh java
