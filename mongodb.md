####NoSQL

NoSQL，指的是非关系型的数据库,用于**超大规模数据**的存储。这些类型的数据存储不需要固定的模式，无需多余操作就可以横向扩展。对NoSQL最普遍的解释是"非关联型的"，强调Key-Value Stores和文档数据库的优点，而不是单纯的反对RDBMS。

#####CAP定理（CAP theorem）or 布鲁尔定理（Brewer's theorem
它指出对于一个分布式计算系统来说，不可能同时满足以下三点:
1. 一致性(Consistency) (所有节点在同一时间具有相同的数据)
2. 可用性(Availability) (保证每个请求不管成功或者失败都有响应)
3. 分隔容忍(Partition tolerance) (系统中任意信息的丢失或失败不会影响系统的继续运作)

#####NoSQL数据库类型
因此，根据 CAP 原理将 NoSQL 数据库分成了满足 CA 原则、满足 CP 原则和满足 AP 原则三 大类：

1. CA - 单点集群，满足一致性，可用性的系统，通常在可扩展性上不太强大。
2. CP - 满足一致性，分区容忍性的系统，通常性能不是特别高。
3. AP - 满足可用性，分区容忍性的系统，通常可能对一致性要求低一些。

具体分类有列存储，文档存储，Key-Value存储，图存储，对象存储，xml数据库。其中MongoDB属于文档存储类：文档存储一般用类似json的格式存储，存储的内容是文档型的。这样也就有有机会对某些字段建立索引，实现关系数据库的某些功能。

#####优缺点
优点:
- 高可扩展性
- 分布式计算
- 低成本
- 架构的灵活性，半结构化数据
- 没有复杂的关系

缺点:
- 没有标准化
- 有限的查询功能（到目前为止）
- 最终一致是不直观的程序

#####BASE
BASE：Basically Available, Soft-state, Eventually Consistent。 由 Eric Brewer 定义。

BASE是NoSQL数据库通常对可用性及一致性的弱要求原则:
1. Basically Availble --基本可用
2. Soft-state --软状态/柔性事务。 "Soft state" 可以理解为"无连接"的, 而 "Hard state" 是"面向连接"的
3. Eventual Consistency -- 最终一致性， 也是是 ACID 的最终目的。

####MongoDB
MongoDB 是由C++语言编写的，是一个基于分布式文件存储的开源数据库系统。旨在为WEB应用提供可扩展的高性能数据存储解决方案。将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。



