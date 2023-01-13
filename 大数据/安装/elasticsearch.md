[TOC]

# config/elasticsearch.yml
```yml
# 集群名称
cluster.name: my-cluster
# 节点名称        
node.name: node-1
#node.attr.rack: r1
path.data: /usr/data/elk/node1
path.logs: /usr/logs/elk/node1
#bootstrap.memory_lock: true
# 配置访问本节点的ip
network.host: 0.0.0.0  
# 设置对外服务的http端口，默认为9200
http.port: 9200
# 设置节点间交互的tcp端口,默认是9300
transport.tcp.port: 9300
# 配置所有用来组建集群的机器的IP地址     
discovery.seed_hosts: ["localhost:9300", "localhost:9301"]
#cluster.initial_master_nodes: ["node-1", "node-2"]
#gateway.recover_after_nodes: 3
#action.destructive_requires_name: true
```


---

# 下载
https://www.elastic.co/downloads/elasticsearch

tar zxvf xxxx.tar 解压

sudo chown -R cai:cai /usr/local/elastic/elasticsearch-8.1.1 赋予执行权限

bin/elasticsearch 启动


错误1:
max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]

vim /etc/sysctl.conf
vm.max_map_count=262145

sysctl -p

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✅ Elasticsearch security features have been automatically configured!
✅ Authentication is enabled and cluster connections are encrypted.

ℹ️  Password for the elastic user (reset with `bin/elasticsearch-reset-password -u elastic`):
  YtEhQbwBJgi_m4DnBbGk

ℹ️  HTTP CA certificate SHA-256 fingerprint:
  5b4d4217d6996214ad8ea2a1cf868eadf2a89847bd7164651f606987f059957a

ℹ️  Configure Kibana to use this cluster:
• Run Kibana and click the configuration link in the terminal when Kibana starts.
• Copy the following enrollment token and paste it into Kibana in your browser (valid for the next 30 minutes):
  eyJ2ZXIiOiI4LjEuMSIsImFkciI6WyIxOTIuMTY4LjUuMTg3OjkyMDAiXSwiZmdyIjoiNWI0ZDQyMTdkNjk5NjIxNGFkOGVhMmExY2Y4NjhlYWRmMmE4OTg0N2JkNzE2NDY1MWY2MDY5ODdmMDU5OTU3YSIsImtleSI6IjY1SWF0MzhCc1JhTS1uRnFhQ0JaOmFRcklKQkhwVFdhY3dFV2JyUnRVUEEifQ==

ℹ️ Configure other nodes to join this cluster:
• Copy the following enrollment token and start new Elasticsearch nodes with `bin/elasticsearch --enrollment-token <token>` (valid for the next 30 minutes):
  eyJ2ZXIiOiI4LjEuMSIsImFkciI6WyIxOTIuMTY4LjUuMTg3OjkyMDAiXSwiZmdyIjoiNWI0ZDQyMTdkNjk5NjIxNGFkOGVhMmExY2Y4NjhlYWRmMmE4OTg0N2JkNzE2NDY1MWY2MDY5ODdmMDU5OTU3YSIsImtleSI6IjdaSWF0MzhCc1JhTS1uRnFhQ0JaOkVVRmhFSHdmVG9HVFRNaUNZUml6b0EifQ==

  If you're running in Docker, copy the enrollment token and run:
  `docker run -e "ENROLLMENT_TOKEN=<token>" docker.elastic.co/elasticsearch/elasticsearch:8.1.1`
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━


kibana

tar 解压
chmod 赋权

vim config/kibana.conf
i18n.locale: "zh-CN"

