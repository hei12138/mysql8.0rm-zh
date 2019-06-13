## 15.2 InnoDB and the ACID Model InnoDB及其ACID模型
- The ACID model is a set of database design principles that emphasize aspects of reliability that are important for business data and mission-critical applications. MySQL includes components such as the InnoDB storage engine that adhere closely to the ACID model, so that data is not corrupted and results are not distorted by exceptional conditions such as software crashes and hardware malfunctions. When you rely on ACID-compliant features, you do not need to reinvent the wheel of consistency checking and crash recovery mechanisms. In cases where you have additional software safeguards, ultra-reliable hardware, or an application that can tolerate a small amount of data loss or inconsistency, you can adjust MySQL settings to trade some of the ACID reliability for greater performance or throughput.
<br/>ACID模型是一组数据库设计原则，注重与保证业务数据和关键任务应用的可靠性。MySQL包含诸如的组件InnoDB存储引擎与ACID模型紧密结合，因此数据不会损坏，并且不会因软件崩溃和硬件故障等特殊情况而导致结果失真。当您依赖符合ACID的功能时，您无需重新发明一致性检查和崩溃恢复机制。如果您有其他软件安全措施，超可靠硬件或可以容忍少量数据丢失或不一致的应用程序，您可以调整MySQL设置以交换一些ACID可靠性以获得更高的性能或吞吐量。

- The following sections discuss how MySQL features, in particular the InnoDB storage engine, interact with the categories of the ACID model:
<br/>以下部分讨论MySQL功能（尤其是InnoDB存储引擎）是如何与ACID模型中的每个分类进行交互的：

A: atomicity.
<br/> A:原子性

C: consistency.
<br/> C:一致性

I: isolation.
<br/> I:隔离性

D: durability.
<br/> D:持久性

Atomicity
<br/> 原子性
The atomicity aspect of the ACID model mainly involves InnoDB transactions. Related MySQL features include:
<br/> ACID模型的原子性方面主要设计到InnoDB的事务特性，相关的MySQL功能包括：

Autocommit setting.
<br/>自动提交设置

COMMIT statement.
<br/> COMMIT语句

ROLLBACK statement.
<br/> ROLLBACK语句

Operational data from the INFORMATION_SCHEMA tables.
<br/> INFORMATION_SCHEMA表中的操作数据

Consistency
<br/>一致性
The consistency aspect of the ACID model mainly involves internal InnoDB processing to protect data from crashes. Related MySQL features include:
<br/> ACID模型 的一致性方面主要涉及到InnoDB的内部处理进程，保护数据不被崩溃影响。相关的MySQL功能包括：

InnoDB doublewrite buffer.
<br/>InnoDB 双写缓冲区。

InnoDB crash recovery.
<br/>InnoDB 崩溃恢复。


Isolation
<br/>隔离性
The isolation aspect of the ACID model mainly involves InnoDB transactions, in particular the isolation level that applies to each transaction. Related MySQL features include:
<br/>ACID模型 的隔离方面主要涉及到InnoDB 事务，特别指每个事务都会用到的隔离级别。相关的MySQL功能包括：

Autocommit setting.
<br/>自动提交设置

SET ISOLATION LEVEL statement.
<br/> SET ISOLATION LEVEL 语句

The low-level details of InnoDB locking. During performance tuning, you see these details through INFORMATION_SCHEMA tables.
<br/>InnoDB 锁定 的底层细节。在性能优化期间，您可以通过INFORMATION_SCHEMA表查看这些详细信息

Durability
<br/>持久性
The durability aspect of the ACID model involves MySQL software features interacting with your particular hardware configuration. Because of the many possibilities depending on the capabilities of your CPU, network, and storage devices, this aspect is the most complicated to provide concrete guidelines for. (And those guidelines might take the form of buy “new hardware”.) Related MySQL features include:
<br/>ACID模型 的持久性方面涉及MySQL软件功能与您的特定硬件配置的交互。由于许多可能行取决于CPU，网络和存储设备的功能，在这方面提供具体的指南是最复杂的。（这些指南可能采取购买“ 新硬件 ”的形式 。）相关的MySQL功能包括：

InnoDB doublewrite buffer, turned on and off by the innodb_doublewrite configuration option.
<br/>InnoDB doublewrite buffer，由innodb_doublewrite 配置选项打开和关闭 。

Configuration option innodb_flush_log_at_trx_commit.
<br/> innodb_flush_log_at_trx_commit配置

Configuration option sync_binlog.
<br/> sync_binlog配置

Configuration option .
<br/> innodb_file_per_table配置

Write buffer in a storage device, such as a disk drive, SSD, or RAID array.
<br/>在存储设备中的写入缓冲区，例如磁盘驱动器，SSD或RAID阵列。

Battery-backed cache in a storage device.
<br/>存储设备中的电池备份缓存。

The operating system used to run MySQL, in particular its support for the fsync() system call.
<br/>用于运行MySQL的操作系统，特别是它对fsync()系统调用的支持。


Uninterruptible power supply (UPS) protecting the electrical power to all computer servers and storage devices that run MySQL servers and store MySQL data.
<br/>不间断电源（UPS）保护运行MySQL服务器和存储MySQL数据的所有计算机服务器和存储设备的电源。

Your backup strategy, such as frequency and types of backups, and backup retention periods.
<br/>您的备份策略，例如备份的频率和类型以及备份保留期。


For distributed or hosted data applications, the particular characteristics of the data centers where the hardware for the MySQL servers is located, and network connections between the data centers.
<br/>对于分布式或托管数据应用程序，MySQL服务器的硬件所在的数据中心的特定特征，以及数据中心之间的网络连接。