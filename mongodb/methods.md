####limit()
limit()方法接受一个数字参数，该参数指定从MongoDB中读取的记录条数。


```
db.COLLECTION_NAME.find().limit(NUMBER)

```
1. 如果你们没有指定limit()方法中的参数则显示集合中的所有数据。

####skip()
使用skip()方法来跳过指定数量的数据，skip方法同样接受一个数字参数作为跳过的记录条数。


```
db.COLLECTION_NAME.find().limit(NUMBER).skip(NUMBER)

```
1. skip()方法默认参数为 0 。

####sort()
对数据进行排序，sort()方法可以通过参数指定排序的字段，并使用 1 和 -1 来指定排序的方式，其中 1 为升序排列，而-1是用于降序排列。


```
db.COLLECTION_NAME.find().sort({KEY:1})
```

