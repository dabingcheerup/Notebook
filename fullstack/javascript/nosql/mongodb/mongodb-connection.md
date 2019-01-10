# 数据库操作

## MongoDB连接

Start Service 只需要在 MongoDB 安装目录的 bin 目录下执行 **mongod**  执行启动操作后，mongodb 在输出一些必要信息后不会输出任何信息，之后就等待连接的建立，当连接被建立后，就会开始打印日志信息。 你可以使用 MongoDB shell 来连接 MongoDB 服务器。你也可以使用 PHP 来连接 MongoDB。

使用 MongoDB shell 来连接 MongoDB 服务器

```text
mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]
```

1. mongodb:// 这是固定的格式，必须要指定。
2. username:password@ 可选项，如果设置，在连接数据库服务器之后，驱动都会尝试登陆这个数据库
3. host1 必须的指定至少一个host, host1 是这个URI唯一要填写的。它指定了要连接服务器的地址。如果要连接复制集，请指定多个主机地址。
4. portX 可选的指定端口，如果不填，默认为27017
5. /database 如果指定username:password@，连接并验证登陆指定数据库。若不指定，默认打开 test 数据库。
6. ?options 是连接选项。如果不使用/database，则前面需要加上/。所有连接选项都是键值对name=value，键值对之间通过&或;（分号）隔开

## 创建数据库

### Syntax

```text
use DATABASE_NAME
```

1. 如果数据库不存在，则创建数据库，否则切换到指定数据库。
2. 要在数据库的列表中显示新建数据库，我们需要向它插入一些数据。
3. MongoDB 中默认的数据库为 test，如果你没有创建新的数据库，集合将存放在 test 数据库中。

## 删除数据库

### Syntax

```text
db.dropDatabase()
```

1. 删除当前数据库，默认为 test，你可以使用 db 命令查看当前数据库名。
2. 通过 show dbs 命令数据库是否删除成功

