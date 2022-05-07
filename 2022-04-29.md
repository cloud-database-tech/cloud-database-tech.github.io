## 重点更新

**Aurora Serverless GA，阿里云公测上线。** 本周，AWS Aurora提供了全新的Serverless能力（v2正式GA）；同时，阿里云RDS MySQL Serverless也已经公测上线，感兴趣的可以去申请试用。AWS Aurora新的Serverless将提供亚秒级（fraction of a second）的扩展能力，为系统压力峰谷明显的应用提供更低的成本。主要场景包括，压力难以预计的系统、多租户的SaaS系统、大型企业内复杂/混合的系统等。当前支持MySQL 8.0和PostgreSQL 13兼容版。不过，这个功能自2020年re:Invent宣布，到现在正式GA，历时一年半，比预期的要久很多。


**常熟农商行核心系统上线OceanBase。** 据可靠消息确认，这次是的银行核心业务切换到OceanBase，还是有里程碑意义的，从公开材料看到，项目周期也非常长，从2018年开始，先是周边系统建立信任，再是十几个月的核心系统改造与测试验证，最终上线，恭喜OceanBase，代表国产数据库走出的坚实的一步。（不确定做业务改造团队是哪家，长亮？改造也是非常关键的一部分）

**袋鼠云推出自主开源计划：DTstackCon。** 开源主要产品包括：

* chunjun(原名FlinkX)--批流一体大数据同步引擎：这是非常不错的项目，2900 stars，不过改名字还是对产品品牌有一定影响的，当然，这可能与Flink本身的品牌保护有关；
* Taier--大数据分布式任务调度系统
* molecule--轻量级Web IDE UI 框架
* 项目地址：https://github.com/DTStack


**BigQuery支持LOAD DATA传输跨云数据。** BigQuery Omni支持使用简单的LOAD DATA语句实现跨云数据传输。通过使用SQL的方式将AWS S3、Azure Blob中的数据安全、高效的导入BigQuery的存储和计算节点中。多云、开源是Google云的核心战略，作为美国市场第三的位置，Google在想各种策略将其他云的数据放到GCP上来计算，大概是Google版的“东数西算”战略吧。

```
LOAD DATA INTO `mydataset.test_csv` (Number INT64, Name STRING, Time DATE)
PARTITION BY Time
FROM FILES (format = 'CSV', uris = ['s3://test-bucket/sampled*'], skip_leading_rows=1)
WITH CONNECTION `aws-us-east-1.test-connection`
```

**华为云发布新的GaussDB品牌视频。** 目前华为云数据库应该算有两个品牌：GaussDB、openGauss，从品牌的角度还是比较容易混淆的，并不利于传播。似乎是这样：GaussDB是华为云上自研的统一数据库品牌，包括了GaussDB for MySQL、for Mongo等。openGauss则是一款开源关系型数据库，一方面外部生态在使用，另一方面华为云GaussDB也基于openGauss推出了对应的产品。另外，注意到，最近华为云正式对外宣布openGauss在邮储银行上线。

**Azure Data Studio新增数据迁移扩展。** Azure Data Studio新增数据迁移扩展，可以帮助用户便捷的将本地管理的SQL Server数据库迁移到Azure的云数据库SQL Server上。Azure Data Studio是由微软提供的开源的、跨平台的SQL Server管理工具。自家的工具都承载着为自家云引流的责任。

**实时数仓SelectDB完成超3亿元融资。** 定位云原生实时数仓厂商，飞轮科技完成超3亿元天使轮和天使+轮融资。创始团队主要来自百度Doris、奇安信大数据等团队。做实时数仓这个方向的团队似乎已经非常多了，是“百家争鸣”还是“军阀混战”，还要再看一段时间。不过据小道报道，Doris后面还会有故事... 拭目以待

## 更新详情

* [Azure] Azure Data Studio新增数据迁移扩展
* [Azure] Cosmos DB for MongoDB提供通过API重建唯一索引的能力
* [AWS]  Aurora Serverless v2 正式GA
* [AWS] Glue提供基于规则匹配和机器学习的敏感信息发现功能
* [AWS] 图数据库Neptune提供免费试用
* [GCP] BigQuery Omni支持使用简单的LOAD DATA语句实现跨云数据传输
* [GCP] Cloud SQL for PostgreSQL开始支持大版本的原地升级功能
* [GCP] BigQuery开始支持使用SEARCH函数的搜索功能
* [OceanBase] OBCA进行了一次升级，更新了考试内容与教材
* [OceanBase] 常熟农商银行核心系统开始上线OceanBase
* [zCloud] 云和恩墨数据库云管平台 zCloud支持OceanBase
* [阿里云] RDS PostgreSQL云盘版只读实例降价，其中包年包月降价幅度45%，按量付费降价幅度17%
* [阿里云] RDS SQL Server企业集群版支持备库可读
* [阿里云] RDS MySQL Serverless 正式上线，免费公测中
* [腾讯云] 云数据库 MySQL支持智能参数调优（内测）
* [腾讯云] 云数据库MySQL支持TXRocks引擎
* [火山云] 云数据库MySQL支持了实例降配功能
* [袋鼠云] 推出自主开源计划：DTstackCon
* [华为云] 华为云数据库发布新的GaussDB品牌视频

**最后，祝大家五一快乐，劳动节多劳动** 
