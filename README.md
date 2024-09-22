# BigData
项目描述：hdfs安装教程

项目启动命令，从编辑中打开
#!/bin/bash
 
read -p "请输入你需要的命令（start or stop or jps）:" userInput

if [ $userInput = "start" ]
then
  echo "启动HDFS环境_start！！！"
  ssh root@linux01 '/opt/module/hadoop-2.6.0/sbin/start-dfs.sh'
  ssh root@linux02 '/opt/module/hadoop-2.6.0/sbin/start-yarn.sh'

  echo "查看集群环境中的进程！！！"
  for ((i=1;i<=3;i++))
  do
    echo "linux0"$i"..............."
    ssh root@linux0$i '/opt/module/jdk1.8.0_411/bin/jps'
  done
elif [ $userInput = "stop" ]
then
  echo "关闭HDFS环境_stop！！！"
  ssh root@linux02 '/opt/module/hadoop-2.6.0/sbin/stop-yarn.sh'
  ssh root@linux01 '/opt/module/hadoop-2.6.0/sbin/stop-dfs.sh'

  echo "查看集群环境中的进程！！！"
  for ((i=1;i<=3;i++))
  do
    echo "linux0"$i"..............."
    ssh root@linux0$i '/opt/module/jdk1.8.0_411/bin/jps'
  done
elif [ $userInput = "jps" ]
then
  echo "查看集群环境中的进程！！！"
  for ((i=1;i<=3;i++))
  do
    echo "linux0"$i"..............."
    ssh root@linux0$i '/opt/module/jdk1.8.0_411/bin/jps'
  done
else
  echo "请输入规范的命令！！！"
fi
