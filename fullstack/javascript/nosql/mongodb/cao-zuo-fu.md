# 操作符

## condition

$gt $gte $lt $lte $ne --------- not equal $eq --------- equal

```text
col"集合中 "likes" 大于100，小于 200 的数据，你可以使用以下命令：

db.col.find({likes : {$lt :200, $gt : 100}})
```

## $type

$type操作符是基于BSON类型来检索集合中匹配的数据类型，并返回结果。

```text
想获取 "col" 集合中 title 为 String 的数据，你可以使用以下命令：

db.col.find({"title" : {$type : 2}})
```

