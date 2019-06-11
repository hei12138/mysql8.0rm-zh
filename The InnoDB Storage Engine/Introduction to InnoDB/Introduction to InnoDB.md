## 15.1 InnoDB介绍




. Each InnoDB table has a primary key index called the clustered index that organizes the data to minimize I/O for primary key lookups. See Section 15.6.2.1, “Clustered and Secondary Indexes” for more information.

- 15.1.1 [Benefits of Using InnoDB Tables](15.1.1 Benefits of Using InnoDB Tables.md)
- 15.1.2 Best Practices for InnoDB Tables
- 15.1.3 Verifying that InnoDB is the Default Storage Engine
- 15.1.4 Testing and Benchmarking with InnoDB

InnoDB is a general-purpose storage engine that balances high reliability and high performance. In MySQL 8.0, InnoDB is the default MySQL storage engine. Unless you have configured a different default storage engine, issuing a CREATE TABLE statement without an ENGINE= clause creates an InnoDB table.
<br/>InnoDB是一款在高可靠性和高性能之间取得了平衡的通用存储引擎，在MySQL 8.0中，InnoDB是默认的MySQL存储引擎。除非您配置了不同的默认存​​储引擎，否则使用不带"ENGINE= "子句的CREATE TABLE的语句将会创建InnoDB表。
### Key Advantages of InnoDB <br/>InnoDB的主要优势

- Its DML operations follow the ACID model, with transactions featuring commit, rollback, and crash-recovery capabilities to protect user data. See Section 15.2, “InnoDB and the ACID Model” for more information.
<br/>InnoDB的DML语句遵循事务ACID模型，使用事务特性commit,rollback,以及crash-recovery(崩溃恢复)功能来保护用户数据,See Section 15.2, “InnoDB and the ACID Model” for more information.

- Row-level locking and Oracle-style consistent reads increase multi-user concurrency and performance. See Section 15.7, “InnoDB Locking and Transaction Model” for more information.
<br/>行级锁及ORACLE风格的`一致性读取`提升多用户下的并发和性能。 See Section 15.7, “InnoDB Locking and Transaction Model” for more information.

- InnoDB tables arrange your data on disk to optimize queries based on primary keys. Each InnoDB table has a primary key index called the clustered index that organizes the data to minimize I/O for primary key lookups. See Section 15.6.2.1, “Clustered and Secondary Indexes” for more information.
<br/>InnoDB表对磁盘上的数据进行排序，以优化基于主键的查询，每个InnoDB表都有一个被称为“聚集索引”的主键索引来组织数据，以最小化主键查找的I/O时间

- To maintain data integrity, InnoDB supports FOREIGN KEY constraints. With foreign keys, inserts, updates, and deletes are checked to ensure they do not result in inconsistencies across different tables. See Section 15.6.1.5, “InnoDB and FOREIGN KEY Constraints” for more information.
<br/>为保证数据完整性，InnoDB支持外键约束，当定义了外键时，insert,update,delete语句将会检查外键约束，以防止不同的表之间出现数据不一致的问题

Table 15.1 InnoDB Storage Engine Features
<br/>表15.1 InnoDB存储引擎的特性

|特性 <br/> Feature|是否支持 <br/> Support|
|---|---|
|B-tree索引|Yes|
|备份/按时间恢复(在MySQL服务器中实现，而不是在InnoDB引擎中实现)|Yes|
|集群支持|No|
|聚集索引|Yes|
|数据压缩|Yes
|数据缓存|Yes|
|数据加密|Yes (通过加密功能在服务器中实现,在MySQL 5.7及更高版本中, 还支持静态数据表空间（data-at-rest tablespace）加密)|
|外键支持|Yes|
|全文搜索索引|Yes (在 MySQL 5.6及更高版本中支持)|
|地理空间(Geospatial)数据类型支持|Yes|
|地理空间索引支持|Yes (在 MySQL 5.7及更高版本中支持)|
|Hash索引|No (InnoDB在内部利用哈希索引来实现其自适应哈希索引功能)|
|索引缓存|Yes|
|锁定粒度|Row|
|MVCC(Multi-Version Concurrency Control)多版本并发控制|Yes|
|复制 (在MySQL服务器中实现，而不是在InnoDB引擎中实现)|Yes|
|存储|最大64TB|
|T-tree索引|No|
|事务|Yes|
|更新数据字典的统计数据Update statistics for data dictionary|Yes|

To compare the features of InnoDB with other storage engines provided with MySQL, see the Storage Engine Features table in Chapter 16, Alternative Storage Engines.
<br/>如果想对比InnoDB与MySQL提供的其他存储引擎的特性,查看第16章（备用存储引擎）存储引擎特性表

### InnoDB Enhancements and New Features <br/>InnoDB增强功能及新特性

For information about InnoDB enhancements and new features, refer to:
<br/>有关InnoDB增强功能和新功能的信息，请参阅：
    
- The InnoDB enhancements list in [Section 1.4, “What Is New in MySQL 8.0”].
    <br/>第1.4节“MySQL 8.0中的InnoDB功能”中 的增强功能列表 

- The [Release Notes.]

### Additional InnoDB Information and Resources <br/>额外的InnoDB信息和资源

- For InnoDB-related terms and definitions, see the MySQL Glossary.
<br/>有关InnoDB相关术语和定义，请参阅MySQL词汇表。

- For a forum dedicated to the InnoDB storage engine, see [MySQL论坛::InnoDB](http://forums.mysql.com/list.php?22).
<br/>对于专用于InnoDB存储引擎的论坛，请参阅 MySQL论坛:: InnoDB。

- InnoDB is published under the same GNU GPL License Version 2 (of June 1991) as MySQL. For more information on MySQL licensing, see http://www.mysql.com/company/legal/licensing/.
<br/>InnoDB以与MySQL相同的GNU GPL许可证版本2（1991年6月）发布。有关MySQL许可的更多信息，请 访问http://www.mysql.com/company/legal/licensing/
