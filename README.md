# 开源分布式系统清单（Distributed System List）

按用途整理常见的开源分布式系统及其官方入口。本清单用于技术选型的初步调研，不代表性能排名或项目推荐。

> 最后核对：2026-09-01；“主要语言”仅指服务端或核心实现，不包含全部客户端、插件和管理界面。

## 收录原则

- 项目应支持多节点协同、横向扩展、复制、分片或容错中的至少一项。
- 主清单优先收录使用 OSI 认可许可证、仍可获得维护版本的项目。
- 已退休或归档的项目移至[历史项目](#历史项目)，源码可见但使用受限的项目移至[源码可用但非-osi-开源](#源码可用但非-osi-开源)。
- 一个项目可能横跨多个领域；为避免重复，放在最能体现其核心用途的分类中。

## 目录

- [分布式存储](#分布式存储)
- [消息队列与事件流](#消息队列与事件流)
- [批处理、流处理与数据集成](#批处理流处理与数据集成)
- [资源管理、调度与云平台](#资源管理调度与云平台)
- [分布式数据库](#分布式数据库)
- [OLAP 与分布式 SQL 查询引擎](#olap-与分布式-sql-查询引擎)
- [分布式缓存](#分布式缓存)
- [协调、服务发现与配置中心](#协调服务发现与配置中心)
- [分布式 ID](#分布式-id)
- [日志与可观测性](#日志与可观测性)
- [分布式机器学习与通用计算](#分布式机器学习与通用计算)
- [Kubernetes Operators](#kubernetes-operators)
- [源码可用但非 OSI 开源](#源码可用但非-osi-开源)
- [历史项目](#历史项目)

## 分布式存储

### 数据访问、缓存与版本管理层

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Alluxio](https://www.alluxio.io/) | Java | 位于计算与底层存储之间的数据访问和缓存层 |
| [Fluid](https://fluid-cloudnative.github.io/) | Go | 面向 Kubernetes 的数据编排与缓存加速 |
| [lakeFS](https://lakefs.io/) | Go | 为对象存储提供类 Git 的数据版本管理；本身不是对象存储 |

### 文件、对象与内容寻址存储

| 项目 | 主要语言 | 类型 |
| --- | --- | --- |
| [Ceph](https://github.com/ceph/ceph) | C++ | 统一的对象、块和文件存储 |
| [Apache HDFS](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsDesign.html) | Java | 面向大文件和高吞吐访问的分布式文件系统 |
| [Apache Ozone](https://ozone.apache.org/) | Java | Hadoop 生态的分布式对象存储 |
| [MinIO](https://github.com/minio/minio) | Go | 兼容 S3 API 的对象存储；社区版目前仅发布源码，不再提供预编译版本 |
| [SeaweedFS](https://github.com/seaweedfs/seaweedfs) | Go | 文件、对象及键值存储 |
| [JuiceFS](https://juicefs.com/docs/community/introduction/) | Go | 构建在对象存储之上的 POSIX 文件系统 |
| [CubeFS](https://www.cubefs.io/) | Go | 云原生分布式文件与对象存储 |
| [Curve](https://github.com/opencurve/curve) | Go / C++ | 分布式块与文件存储 |
| [GlusterFS](https://www.gluster.org/) | C | 通用分布式文件系统 |
| [Lustre](https://www.lustre.org/) | C | 面向 HPC 的并行文件系统 |
| [MooseFS](https://moosefs.com/) | C | 通用容错分布式文件系统 |
| [LizardFS](https://github.com/lizardfs/lizardfs) | C++ | MooseFS 衍生的分布式文件系统 |
| [OpenAFS](https://www.openafs.org/) | C | AFS 协议的分布式文件系统实现；原清单中的 `OpenFS` 为误写 |
| [Tahoe-LAFS](https://tahoe-lafs.org/) | Python | 去中心化、端到端加密的文件存储 |
| [Garage](https://garagehq.deuxfleurs.fr/) | Rust | 面向自托管场景的轻量级 S3 对象存储 |
| [IPFS / Kubo](https://github.com/ipfs/kubo) | Go | 点对点内容寻址网络，不是传统共享文件系统 |
| [LeoFS](https://github.com/leo-project/leofs) | Erlang | 兼容 S3 API 的分布式对象存储 |
| [Quantcast File System](https://github.com/quantcast/qfs) | C++ | 面向大规模 MapReduce 工作负载的文件系统 |
| [XtreemFS](https://github.com/xtreemfs/xtreemfs) | Java / C++ | 跨地域分布式文件系统；采用前应先评估维护活跃度 |

延伸参考：[Wikipedia：分布式文件系统比较](https://en.wikipedia.org/wiki/Comparison_of_distributed_file_systems)、[OSS Insight：Distributed File Storage](https://ossinsight.io/collections/distributed-file-storage/)。

## 消息队列与事件流

### Broker 与事件流平台

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Apache Kafka](https://kafka.apache.org/) | Java | 分布式事件流、持久化日志和流处理平台 |
| [Apache Pulsar](https://pulsar.apache.org/) | Java | 计算与存储分离的消息和事件流平台 |
| [Apache RocketMQ](https://rocketmq.apache.org/) | Java | 分布式消息与事件流平台 |
| [RabbitMQ](https://www.rabbitmq.com/) | Erlang | 支持 AMQP 等协议的消息代理 |
| [Apache ActiveMQ](https://activemq.apache.org/) | Java | 包含 ActiveMQ Classic 与 Artemis 的消息代理项目 |
| [NATS](https://nats.io/) | Go | 轻量级消息系统；JetStream 提供持久化和复制 |
| [NSQ](https://nsq.io/) | Go | 去中心化的实时分布式消息平台 |
| [QMQ](https://github.com/qunarcorp/qmq) | Java | 去哪儿开源的分布式消息中间件 |

### 消息通信库

[ZeroMQ](https://zeromq.org/)（C++）和 [JeroMQ](https://github.com/zeromq/jeromq)（Java）是消息通信库，不是可独立部署的分布式 Broker，因此不与上表混为一类。

## 批处理、流处理与数据集成

### 分布式计算引擎

| 项目 | 主要语言 | 模型 |
| --- | --- | --- |
| [Apache Spark](https://spark.apache.org/) | Scala / Java | 批处理、流处理、SQL 与机器学习 |
| [Apache Flink](https://flink.apache.org/) | Java | 有状态流处理及有界流（批）处理 |
| [Apache Beam](https://beam.apache.org/) | Java / Python / Go | 可运行在多种执行引擎上的统一编程模型 |
| [Hadoop MapReduce](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html) | Java | Hadoop 的经典批处理模型 |
| [Apache Tez](https://tez.apache.org/) | Java | 构建在 YARN 上的 DAG 数据处理框架 |
| [Apache Storm](https://storm.apache.org/) | Java / Clojure | 分布式实时流计算 |
| [Apache Samza](https://samza.apache.org/) | Java / Scala | 有状态流处理框架 |

### 数据集成与变更捕获

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Apache Gobblin](https://gobblin.apache.org/) | Java | 批式与流式数据集成 |
| [Debezium](https://debezium.io/) | Java | 数据库变更数据捕获（CDC）；不是数据库 |
| [Apache NiFi](https://nifi.apache.org/) | Java | 可视化数据流编排与传输 |
| [Apache SeaTunnel](https://seatunnel.apache.org/) | Java | 批流一体的数据集成平台 |
| [Apache Flume](https://flume.apache.org/) | Java | 分布式日志及事件采集 |
| [Loggie](https://github.com/loggie-io/loggie) | Go | 云原生日志采集 |
| [Fluent Bit](https://fluentbit.io/) | C | 轻量级日志、指标和链路数据处理器 |
| [Fluentd](https://www.fluentd.org/) | Ruby / C | 统一日志采集层 |
| [Vector](https://vector.dev/) | Rust | 可观测数据管道 |

## 资源管理、调度与云平台

### 集群资源管理与调度

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Kubernetes](https://kubernetes.io/) | Go | 容器编排与集群资源管理 |
| [Apache Hadoop YARN](https://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html) | Java | Hadoop 集群资源管理与任务调度 |
| [Volcano](https://volcano.sh/) | Go | Kubernetes 原生批处理和高性能工作负载调度 |
| [Karmada](https://karmada.io/) | Go | 多 Kubernetes 集群编排 |
| [Slurm](https://slurm.schedmd.com/) | C | HPC 与大规模计算集群的作业调度和资源管理 |

### 云计算平台

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Apache CloudStack](https://cloudstack.apache.org/) | Java | IaaS 云计算平台 |
| [OpenStack](https://www.openstack.org/) | Python | 数据中心云基础设施平台 |
| [OpenNebula](https://opennebula.io/) | C++ / Ruby | 私有云和边缘云管理平台 |

## 分布式数据库

### 分布式 SQL、分片与事务型数据库

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [TiDB](https://www.pingcap.com/tidb/) | Go | 兼容 MySQL 协议的分布式 SQL 数据库 |
| [YugabyteDB](https://www.yugabyte.com/yugabytedb/) | C++ / Java | 兼容 PostgreSQL/Cassandra API 的分布式数据库 |
| [OceanBase](https://github.com/oceanbase/oceanbase) | C++ | 分布式关系数据库 |
| [Vitess](https://vitess.io/) | Go | MySQL 水平扩展与分片中间件 |
| [Apache ShardingSphere](https://shardingsphere.apache.org/) | Java | 数据库分片、治理和分布式事务生态 |
| [Citus](https://www.citusdata.com/) | C | PostgreSQL 分布式扩展 |
| [rqlite](https://rqlite.io/) | Go | 基于 SQLite 和 Raft 的轻量级分布式关系数据库 |

### 键值、宽列、文档与图数据库

| 项目 | 主要语言 | 类型 |
| --- | --- | --- |
| [TiKV](https://tikv.org/) | Rust | 支持事务的分布式键值存储 |
| [FoundationDB](https://www.foundationdb.org/) | C++ | 有序、事务型分布式键值数据库 |
| [Apache HBase](https://hbase.apache.org/) | Java | 基于 HDFS 的分布式宽列数据库；原清单中的 `HBAse` 为误写 |
| [Apache Cassandra](https://cassandra.apache.org/) | Java | 去中心化宽列数据库 |
| [Apache Accumulo](https://accumulo.apache.org/) | Java | 基于 Hadoop、ZooKeeper 的有序宽列存储 |
| [Apache CouchDB](https://couchdb.apache.org/) | Erlang | 支持多主复制的文档数据库 |
| [eXist-db](https://exist-db.org/) | Java | XML 原生数据库 |
| [NebulaGraph](https://www.nebula-graph.io/) | C++ | 分布式图数据库 |
| [JanusGraph](https://janusgraph.org/) | Java | 使用外部存储后端的分布式图数据库 |
| [Apache HugeGraph](https://hugegraph.apache.org/) | Java | 分布式图数据库 |

`Apache Phoenix` 是 HBase 之上的 SQL 层，不是独立数据库，参见 [Apache Phoenix](https://phoenix.apache.org/)。

## OLAP 与分布式 SQL 查询引擎

### OLAP、MPP 数据库与分析存储

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [ClickHouse](https://clickhouse.com/clickhouse) | C++ | 列式 OLAP 数据库 |
| [Apache Doris](https://doris.apache.org/) | Java / C++ | 实时分析型 MPP 数据库 |
| [Apache Druid](https://druid.apache.org/) | Java | 实时分析数据库；已从原“分布式数据库”分类移入此处 |
| [Apache Pinot](https://pinot.apache.org/) | Java | 低延迟实时 OLAP 数据库 |
| [StarRocks](https://www.starrocks.io/) | Java / C++ | 实时分析型 MPP 数据库 |
| [Apache Kylin](https://kylin.apache.org/) | Java | 面向大数据的多维分析平台 |
| [Apache Kudu](https://kudu.apache.org/) | C++ | 面向快速分析的分布式列式存储引擎 |
| [Apache Cloudberry](https://cloudberry.apache.org/) | C | 基于 PostgreSQL 的 MPP 数据库 |

### 查询引擎与 SQL 框架

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Trino](https://trino.io/) | Java | 跨异构数据源的分布式 SQL 查询引擎 |
| [PrestoDB](https://prestodb.io/) | Java / C++ | 分布式 SQL 查询引擎；与 Trino 是两个独立项目 |
| [Apache Hive](https://hive.apache.org/) | Java | Hadoop 数据仓库与 SQL 引擎 |
| [Apache Drill](https://drill.apache.org/) | Java | 面向多种存储的无模式 SQL 查询引擎 |
| [Apache Impala](https://impala.apache.org/) | C++ / Java | Hadoop 生态的 MPP SQL 查询引擎 |
| [Apache Calcite](https://calcite.apache.org/) | Java | 查询解析、优化和执行框架；不是独立 OLAP 数据库 |
| [Apache Kyuubi](https://kyuubi.apache.org/) | Scala / Java | 面向 Spark/Flink 的分布式 SQL 网关 |
| [Spark SQL](https://spark.apache.org/sql/) | Scala / Java | Apache Spark 的结构化数据处理模块 |
| [Flink SQL](https://nightlies.apache.org/flink/flink-docs-stable/docs/dev/table/sql/overview/) | Java | Apache Flink 的流批统一 SQL 层 |

## 分布式缓存

| 项目 | 主要语言 | 说明 |
| --- | --- | --- |
| [Redis](https://redis.io/) | C / C++ | 内存数据结构存储，支持复制、哨兵和 Cluster；Redis 8 起可选 AGPLv3 |
| [Valkey](https://valkey.io/) | C | Redis 7.2 的 BSD-3-Clause 社区分支，支持集群模式 |
| [Apache Ignite](https://ignite.apache.org/) | Java | 分布式内存计算、缓存和数据库平台 |
| [Apache Geode](https://geode.apache.org/) | Java | 分布式内存数据管理平台 |
| [Memcached](https://memcached.org/) | C | 单节点缓存服务；通常依靠客户端一致性哈希组成分布式缓存 |

原清单中的 [Chronicle Map](https://github.com/OpenHFT/Chronicle-Map) 是单 JVM 的持久化堆外 Map；其开源核心本身不提供通用的集群复制，因此不再把它列作分布式内存数据库。

## 协调、服务发现与配置中心

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Apache ZooKeeper](https://zookeeper.apache.org/) | Java | 分布式协调和一致性服务 |
| [etcd](https://etcd.io/) | Go | 基于 Raft 的一致性键值存储 |
| [Nacos](https://nacos.io/) | Java | 服务发现、配置和服务管理 |
| [Eureka](https://github.com/Netflix/eureka) | Java | REST 服务发现组件 |
| [Atomix](https://github.com/atomix/atomix) | Go | 面向 Kubernetes 分布式应用的运行时；原 Java 实现已归档 |

## 分布式 ID

| 项目 | 主要语言 | 算法/形态 |
| --- | --- | --- |
| [Leaf](https://github.com/Meituan-Dianping/Leaf) | Java | 号段模式与 Snowflake 模式的 ID 服务 |
| [Sonyflake](https://github.com/sony/sonyflake) | Go | Sony 开源的 Snowflake 风格 ID 生成器 |
| [UidGenerator](https://github.com/baidu/uid-generator) | Java | 百度开源的 Snowflake 风格生成器 |
| [Tinyid](https://github.com/didi/tinyid) | Java | 滴滴开源的分布式 ID 服务 |

Snowflake 最初指 Twitter 公开的 ID 生成算法/方案，并不是 Sony 的 Go 项目；原清单中的 `Snowflake(golang) (sony)` 实际应为 Sonyflake。

## 日志与可观测性

### 分布式日志存储

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Apache BookKeeper](https://bookkeeper.apache.org/) | Java | 低延迟、持久化的复制日志存储 |
| [Pravega](https://www.pravega.io/) | Java | 面向连续、无界数据的分布式流存储 |
| [Grafana Loki](https://grafana.com/oss/loki/) | Go | 水平扩展、高可用的日志聚合系统 |

### 监控、指标、链路与时序数据

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Prometheus](https://prometheus.io/) | Go | 监控与时序数据库；单实例为主，常结合 Thanos/Cortex/Mimir 扩展 |
| [Thanos](https://thanos.io/) | Go | Prometheus 的高可用、长期存储和全局查询层 |
| [Cortex](https://cortexmetrics.io/) | Go | 多租户、水平扩展的 Prometheus 后端 |
| [Grafana Mimir](https://grafana.com/oss/mimir/) | Go | 多租户、长期存储的 Prometheus 后端 |
| [VictoriaMetrics](https://victoriametrics.com/) | Go | 时序数据库与监控方案，提供集群部署模式 |
| [Apache IoTDB](https://iotdb.apache.org/) | Java | 面向物联网的分布式时序数据库 |
| [M3](https://m3db.io/) | Go | 分布式时序数据库与查询引擎 |
| [OpenTSDB](https://opentsdb.net/) | Java | 构建在 HBase 上的分布式时序数据库 |
| [TDengine](https://tdengine.com/) | C | 面向物联网和工业场景的时序数据库 |
| [Apache SkyWalking](https://skywalking.apache.org/) | Java | 分布式追踪、指标、日志和 APM 平台 |
| [OpenTelemetry](https://opentelemetry.io/) | Go / Java 等 | 可观测数据的 API、SDK、语义约定和 Collector |

## 分布式机器学习与通用计算

| 项目 | 主要语言 | 定位 |
| --- | --- | --- |
| [Apache Mahout](https://mahout.apache.org/) | Scala / Java / C++ | 分布式线性代数与机器学习；原清单中的 `mathout` 为误写 |
| [Ray](https://www.ray.io/) | Python / C++ | 分布式 Python 与 AI 应用计算框架 |
| [Dask](https://www.dask.org/) | Python | 并行与分布式 Python 计算 |
| [Horovod](https://horovod.ai/) | Python / C++ | 分布式深度学习训练框架 |
| [DeepSpeed](https://www.deepspeed.ai/) | Python / C++ | 大模型分布式训练与推理优化库 |

## Kubernetes Operators

Operator 是分布式系统的部署和运维自动化工具，而不是一类独立的分布式系统。

| 项目 | 管理对象 |
| --- | --- |
| [Strimzi](https://strimzi.io/) | Apache Kafka |
| [Spark Kubernetes Operator](https://www.kubeflow.org/docs/components/spark-operator/) | Apache Spark |
| [Prometheus Operator](https://prometheus-operator.dev/) | Prometheus 及相关监控组件 |
| [CloudNativePG](https://cloudnative-pg.io/) | PostgreSQL |
| [Zalando Postgres Operator](https://github.com/zalando/postgres-operator) | PostgreSQL |
| [Operator Framework](https://operatorframework.io/) | Operator 的开发、安装和生命周期管理工具集 |

更多项目可参考 [Awesome Operators](https://github.com/operator-framework/awesome-operators)。

## 源码可用但非 OSI 开源

下列项目具有公开源码，但当前版本许可证包含额外使用限制，不应与 OSI 定义的开源软件混称。选型前请直接核对对应版本的许可证。

| 项目 | 主要语言 | 说明 |
| --- | --- | --- |
| [CockroachDB](https://github.com/cockroachdb/cockroach) | Go | 24.3.0 及之后版本采用 CockroachDB Software License |
| [Consul](https://github.com/hashicorp/consul) | Go | HashiCorp 2023 年起的新版本采用 BUSL-1.1 |
| [ScyllaDB](https://github.com/scylladb/scylladb) | C++ | OSS 6.2.x 是最后的 AGPL 开源系列；2025.1 起为源码可用许可证 |

## 历史项目

这些项目适合研究历史架构或维护遗留系统，不建议在未评估替代方案、漏洞修复和社区支持的情况下用于新生产系统。

| 项目 | 原分类 | 状态 |
| --- | --- | --- |
| [Apache Mesos](https://attic.apache.org/projects/mesos.html) | 资源管理 | 2025 年进入 Apache Attic |
| [Apache HAWQ](https://attic.apache.org/projects/hawq.html) | OLAP | 2024 年进入 Apache Attic |
| [Apache Chukwa](https://attic.apache.org/projects/chukwa.html) | 监控/日志采集 | 2020 年进入 Apache Attic |
| [Apache Sqoop](https://attic.apache.org/projects/sqoop.html) | 数据集成（原清单误列为 OLAP） | 2021 年进入 Apache Attic |
| [Scribe](https://github.com/facebookarchive/scribe) | 日志采集 | Facebook 于 2022 年归档 |
| [etcd-operator](https://github.com/coreos/etcd-operator) | Kubernetes Operator | 2020 年归档且不再维护 |

## 参与维护

欢迎提交 Issue 或 Pull Request。新增或更正条目时，请尽量提供：

1. 项目官方主页或官方源码仓库；
2. 核心用途与主要实现语言；
3. 当前许可证；
4. 若项目已停止维护，提供归档或退休公告。

项目状态和许可证会发生变化，生产选型应以项目官方文档及仓库中的最新许可证文件为准。
