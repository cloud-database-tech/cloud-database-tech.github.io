---
layout: post
categories: [other]
my_publishdate: 2022-05-30
my_title: SQL Server 2022公测发布：全面支持云服务的数据库
---
## SQL Server 2022公测发布：全面支持云服务的数据库

在上周，SQL Server 2022版本（16.x）正式进入公测状态，大家都可以下载并安装了。当前只支持Windows，被称为CTP 2.0版本（community technology preview ），包含了企业版的所有功能，可以试用180天。于是第一时间下载并进行了体验，一起来看看，新版本有哪些新的功能吧。

### 全面建立与Azure云的联系

**通过Azure Synapse Link for SQL（[公测](https://techcommunity.microsoft.com/t5/azure-synapse-analytics-blog/announcing-the-public-preview-of-azure-synapse-link-for-sql/ba-p/3372986)）** 支持将SQL Server 2022版本与云端Azure Synapse Analytics无缝集成，从而实现分析、BI和ML等数据处理能力：[参考](https://docs.microsoft.com/en-us/azure/synapse-analytics/synapse-link/sql-synapse-link-overview)。还可以通过Azure SQL Managed Instance的Link功能，实现将云端实例作为本地SQL Server的副本，提供只读或者容灾使用：[参考](https://docs.microsoft.com/en-us/azure/azure-sql/managed-instance/managed-instance-link-feature-overview?view=azuresql) 。

支持使用Azure AD进行数据库的认证：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/azure-ad-authentication-sql-server-overview?view=sql-server-ver16)；支持使用Azure Defender for SQL来保护SQL Server：[参考](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-sql-introduction)。

**支持了S3-协议的对象存储**，备份命令可以直接备份S3兼容的存储上：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/sql-server-backup-to-url-s3-compatible-object-storage?view=sql-server-ver16)。从2012版本开始，已经支持了备份到Azure Blob Storage；2022版本开始支持到S3兼容的存储进行备份。同时，PolyBase功能（[参考](https://docs.microsoft.com/en-us/sql/relational-databases/polybase/polybase-guide?view=sql-server-ver16)）也可以支持S3兼容存储的访问，支持使用T-SQL直接访问parquet文件的数据。

SQL Server安装时，可以直接安装Azure Arc agent：[参考](https://docs.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver16#install-sql-server-from-the-command-prompt)

Azure Data Studio、VS Code等最新版本都开始支持SQL Server 2022；SSMS发布最新的19.0版本。

### 新增了账本数据库(ledger database)功能（[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/ledger/ledger-how-to-configure-ledger-database?view=sql-server-ver16&preserve-view=true&tabs=Portal&pivots=as1-sql-server)）

新增支持了ledger database功能（[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/ledger/ledger-how-to-configure-ledger-database?view=sql-server-ver16&preserve-view=true&tabs=Portal&pivots=as1-sql-server)），提供数据不可篡改的证明，其模式类似于AWS QLDB（[参考](https://aws.amazon.com/qldb/)）。在数据库所有记录的变更都通过递归哈希的Merkle tree记录（被称为Database digests），用户可以通过其他独立的存储保存该[Database digests](https://docs.microsoft.com/en-us/sql/relational-databases/security/ledger/ledger-overview?view=sql-server-ver16#database-digests)，独立存储可以使用Azure Blob Storage或其他写入后不可修改的存储中。在重要的审计、第三方商务流程记录中使用。

### 持续了增强了数据库安全

* 支持使用Azure Defender for SQL保护SQL Server：[参考](https://docs.microsoft.com/en-us/azure/defender-for-cloud/defender-for-sql-introduction)
* 基于最小权限原则，对于某些管理任务新增了新的内置权限与角色：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles?view=sql-server-ver16#fixed-server-level-roles-introduced-in-sql-server-2022)
* 提供了更细粒度（包括database、schema、table或column级别）的UNMASK权限管理：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/dynamic-data-masking?view=sql-server-ver16#granular)
* 更好的支持了对秘钥（数字证书和秘钥）向Azure Blob Storage的备份：[参考](https://docs.microsoft.com/en-us/sql/t-sql/statements/backup-symmetric-key-transact-sql)
* 支持新的TDS 8.0协议，兼容TLS 1.3：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/networking/tds-8-and-tls-1-3?view=sql-server-ver16)
* 增强了Always encrypted数据的加密查询能力，包括 JOIN, GROUP BY, and ORDER BY等：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sql-server-ver16) 

### 继续提升数据库性能

* 备节点上支持与主节点上一样的Query Store功能，帮助用户管理与诊断Query的执行计划相关的问题：[参考](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2022?view=sql-server-ver16#query-store-improvements)
* 开始支持Query Store hints功能（注：之前仅Azure云端版本支持）：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/performance/query-store-hints?view=sql-server-ver16)
* 增强了Memory Grant Feedback (MGF) 功能，帮助
* 提升了大内存场景下的内存管理能力，避免OOM发生
* 提供了大内存场景下，内存池并行扫描的能力：[参考](https://docs.microsoft.com/en-us/troubleshoot/sql/performance/buffer-pool-scan-runs-slowly-large-memory-machines)
* 提供了参数-自感知缓存执行计划能力，帮助SQL Server自动化的处理由于参数分布带来的无法使用最优执行计划的问题：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/performance/parameter-sensitivity-plan-optimization?view=sql-server-ver16)
* 创建表语句新增了XML_COMPRESSION选项，提供XML压缩能力：[参考](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-table-transact-sql?view=sql-server-ver16)
* 提供新的硬件感知和使用能力，例如使用高级向量扩展指令集（Advanced Vector Extensions）
* DOP功能提供新的参数DOP_FEEDBACK，帮助更加自动化管理DOP参数的配置：[参考](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option?view=sql-server-ver16)
* 提供了Cardinality estimation feedback，帮助定位由于基数预估不准确导致的性能问题：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/performance/cardinality-estimation-sql-server?view=sql-server-ver16)
* 提供了基于Query Store功能的强制执行计划选择能力：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/performance/optimized-plan-forcing-query-store?view=sql-server-ver16)

### 增强数据库的可用性与可管理性

* 提供了"contained availability group"（[What is a contained availability group?](https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/contained-availability-groups-overview?view=sql-server-ver16)），在AG层面提供了自己的元数据管理、并且包含了需要的一些系统数据库等内容。
* 支持了AG参数REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT的修改：[参考](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-availability-group-transact-sql?view=sql-server-ver16) 。
* 在SQL Server初始安装时，可以直接安装Azure Arc agent：[参考](https://docs.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver16#install-sql-server-from-the-command-prompt)
* 进一步优化了ADR功能（Accelerated Database Recovery），开启后数据库在异常恢复时能够更快，提升整体可用性：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-and-recovery-overview-sql-server?view=sql-server-ver16#adr)
* 提升快照备份能力，新增了使用T-SQL冻结IO操作：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/create-a-transact-sql-snapshot-backup?view=sql-server-ver16)
* 新增参数降低数据库收缩（空间回收）是对数据库并发读写的影响：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/databases/shrink-a-database?view=sql-server-ver16#remarks)
* 新增了数据库级别变量实现异步的统计信息更新，以降低对数据库并发读写的影响：[参考](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-scoped-configuration-transact-sql?view=sql-server-ver16)
* 支持数据备份到S3兼容的存储中，也可以直接从这类存储中恢复数据：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/sql-server-backup-to-url-s3-compatible-object-storage?view=sql-server-ver16)

### 更多细节功能增强

* 新增更多的JSON相关的函数：ISJSON、JSON_ARRAY、JSON_OBJECT、JSON_PATH_EXISTS等
* 新增了部分处理时序数据的函数，例如DATE_BUCKET、GENERATE_SERIES等
* 新增SELECT...WINDOW语法：[参考](https://docs.microsoft.com/en-us/sql/t-sql/queries/select-window-transact-sql?view=sql-server-ver16)
* ALTER TABLE ADD CONSTRAINT支持中断后续执行：[参考](https://docs.microsoft.com/en-us/sql/relational-databases/security/resumable-add-table-constraints?view=sql-server-ver16)
* 新增部分聚合和字符处理函数：GREATEST、LEAST、STRING_SPLIT
* Azure Data Studio、VS Code最新版本都开始支持SQL Server 2022；SSMS发布最新的19.0版本；
