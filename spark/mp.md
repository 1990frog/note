mapper
redducer

通过driver把mapper和reducer串联

会花费非常多的时间在非业务逻辑

---

input=>mapreduce=>output=>mapreduce=>output

maptask或者reducetask都是进程级别
第一个mr对的输出要落地，然后第二个mr把第一个mr的输出当做输入。中间过程的数据是要落地


spark运行模式
local：本地运行
standalone：hadoop部署多个节点，同理spoark可以部署多个节点
yarn：将spark作业提交到hadoop（yarn）集群中运行
mesos
k8s

spark 提供了n个高阶api


mvn archetype:generate -DarchetypeGroupId=net.alchim31.maven -DarchetypeArtifactId=scala-archetype-simple




