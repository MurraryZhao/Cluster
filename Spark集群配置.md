![img](C:%5Csoftware%5CTypora%5Cimage%5C%5D2KT0%25T$TB%60K%5BF9%7B6LVUA.jpg)

# Spark集群配置

## NOTES

* <u>***进行下一步之前要先检查上一步的目标是否达成***</u> 
* <u>***以下操作未特殊说明的均在主节点进行***</u>
* <u>***参考文档仅作参考，根据实际情况进行配置***</u>
* <u>***进行删改操作之前建议对配置文件进行备份***</u>
* <u>***设计其他详细命令及操作可参考其他文档***</u>
## 修改配置文件
```
cd /opt/spark-2.2.0-bin-hadoop2.7/conf/
vim slaves
```

![image-20201122135915827](C:%5Csoftware%5CTypora%5Cimage%5Cimage-20201122135915827.png)
```
vim spark-env.sh
```

![image-20201122140116556](C:%5Csoftware%5CTypora%5Cimage%5Cimage-20201122140116556.png)

发送给其他节点
```
cd /opt/spark-2.2.0-bin-hadoop2.7
scp -r conf ubuntu2:/opt/spark-2.2.0-bin-hadoop2.7
scp -r conf ubuntu3:/opt/spark-2.2.0-bin-hadoop2.7
```

## 启动spark集群

```
cd /opt/spark-2.2.0-bin-hadoop2.7/sbin
./start-all.sh
```
启动成功后在浏览器输入localhost:8080查看集群状态

![2020-11-22_154957](C:%5Csoftware%5CTypora%5Cimage%5C2020-11-22_154957.png)


## 进入spark-shell
```
cd /opt/spark-2.2.0-bin-hadoop2.7/bin
./spark-shell --master spark://ubuntu1:7077
```
不使用这个命令进入spark-shell的话还是用单机模式



执行完成后可查看详细内容

![2020-11-22_155423](C:%5Csoftware%5CTypora%5Cimage%5C2020-11-22_155423.png)

## 其它



## 问题及解决

* 注意在spark集群环境下读取或写入数据不要用localhost
* 出现命令未找到一般用下面这个命令就能解决
```
source /etc/profile
```

## 参考文档：

spark集群配置https://www.cnblogs.com/yanshw/p/11614988.html

https://blog.csdn.net/zkhong07/article/details/94993053

* * *
>@author MurrayZhao  感谢指正