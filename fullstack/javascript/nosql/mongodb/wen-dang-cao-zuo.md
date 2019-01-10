# 文档操作

## Insert doc to collection

所有存储在集合中的数据\(doc\)都是BSON格式。BSON是一种类json的一种二进制形式的存储格式,简称Binary JSON。

```text
db.collectionName.insert(doc)
```

1. 如果该集合不在该数据库中， MongoDB 会自动创建该集合并插入文档。

查看已插入文档

```text
db.collectionName.find()
```

可以将数据定义为一个变量

```text
> document=({title: 'MongoDB 教程', 
    description: 'MongoDB 是一个 Nosql 数据库',
    by: '菜鸟教程',
    url: 'http://www.runoob.com',
    tags: ['mongodb', 'database', 'NoSQL'],
    likes: 100
});
```

其他插入方法： 1. db.col.save\(document\): 如果不指定 \_id 字段 save\(\) 方法类似于 insert\(\) 方法。如果指定 \_id 字段，则会更新该 \_id 的数据 2. db.collection.insertOne\(\): 向指定集合中插入一条文档数据 3. db.collection.insertMany\(\): 向指定集合中插入多条文档数据

## Update doc\(two ways\)

1. update

```text
db.collection.update(
   <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>
   }
)
```

参数说明： query : update的查询条件，类似sql update查询内where后面的。 update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的 upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。 multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。 writeConcern :可选，抛出异常的级别。

1. save\(\)

```text
db.collection.save(
   <document>,
   {
     writeConcern: <document>
   }
)
```

参数说明： document : 文档数据。 writeConcern :可选，抛出异常的级别。

3.2后更新集合文档的方法 1. db.collection.updateOne\(\) 向指定集合更新单个文档 2. db.collection.updateMany\(\) 向指定集合更新多个文档

## Delete doc

deleteOne\(\) 和 deleteMany\(\) 方法。

如删除集合下全部文档：

db.inventory.deleteMany\({}\) 删除 status 等于 A 的全部文档：

db.inventory.deleteMany\({ status : "A" }\) 删除 status 等于 D 的一个文档：

db.inventory.deleteOne\( { status: "D" } \) 1. 在执行remove\(\)函数前先执行find\(\)命令来判断执行的条件是否正确，这是一个比较好的习惯。

## search doc

```text
db.collection.find(query, projection)
```

query ：可选，使用查询操作符指定查询条件 projection ：可选，使用投影操作符指定返回的键。查询时返回文档中所有键值， 只需省略该参数即可（默认省略）。

pretty\(\) 方法以格式化的方式来显示所有文档。

```text
db.col.find().pretty()
```

### =SQL Where

```text
等于    {<key>:<value>}    db.col.find({"by":"菜鸟教程"}).pretty()    where by = '菜鸟教程'
小于    {<key>:{$lt:<value>}}    db.col.find({"likes":{$lt:50}}).pretty()    where likes < 50
小于或等于    {<key>:{$lte:<value>}}    db.col.find({"likes":{$lte:50}}).pretty()    where likes <= 50
大于    {<key>:{$gt:<value>}}    db.col.find({"likes":{$gt:50}}).pretty()    where likes > 50
大于或等于    {<key>:{$gte:<value>}}    db.col.find({"likes":{$gte:50}}).pretty()    where likes >= 50
不等于    {<key>:{$ne:<value>}}
```

### =SQL And

MongoDB 的 find\(\) 方法可以传入多个键\(key\)，每个键\(key\)以逗号隔开，即常规 SQL 的 AND 条件。

```text
db.col.find({key1:value1, key2:value2}).pretty
```

### =SQL OR

A or B = $or: \[A,B\]

```text
db.col.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```

### Projection

