**USING PYTHON...**

**Database Connection**

```
# database name = myFlask
# collection name = latest_log

client = MongoClient("mongodb://axis3.ter.teradyne.com:27020/myFlask")
db = client.myFlask
latest_log = db.latest_log
```

**Select the last doc in a collection**

```
# Pipeline
last_sec_dict = latest_log.find_one({"daemon":vendor}, sort=[("_id", -1)])
# find_one() return a dictionary
# find() return a list of result
```

**Query the string type date **

```
db.collection.find({"createdAt": { $gte : new ISODate("2017-05-15T02:08:48.419+05:30") }})
# or use variable
var today = new Date();
>>today
>>ISODate("2012-11-26T22:12:03.870Z")
var yesterday = new Date()
yesterday.setDate(today.getDate() - 1)
>>yesterday
>>ISODate("2012-11-25T22:12:03.870Z")
db.collection.find({"createdAt": { $gte : yesterday, $lt : today }})
```

[**Query the datetime type date**](https://stackoverflow.com/questions/11957595/mongodb-pymongo-query-with-datetime)

```
start = datetime.datetime(2012, 2, 2, 6, 35, 6, 764)
end = datetime.datetime(2012, 2, 2, 6, 55, 3, 381)

for doc in db.wing_model.find({'time': {'$gte': start, '$lt': end}}):
    print doc
```

[**Create an ISODate **](https://stackoverflow.com/questions/7651064/create-an-isodate-with-pymongo)

```
>>> c.test.test.insert({'date': datetime.datetime.utcnow()})
ObjectId('4e8b388367d5bd2de0000000')
>>> c.test.test.find_one()
{u'date': datetime.datetime(2011, 10, 4, 16, 46, 59, 786000), u'_id': ObjectId('4e8b388367d5bd2de0000000')}
```

**Check a field if exists**

```
collection.find({"field": {'$exists': True}}]})
```

[**Insert additional obj into collection**](https://stackoverflow.com/questions/17288439/mongodb-how-to-insert-additional-object-into-object-collection)

```
db.stack.update(
  { ownerEmail: "john.smith@gmail.com" },
  {
    $push: {
      camps: { name: "cubs-killeen", location: "some other Place" }
    }
  }
);
```

[**Add key-value pair or a new field to an obj**](https://stackoverflow.com/questions/38887155/how-to-add-key-value-pair-to-object-in-mongodb)

```
Before:
  {
    ...
    Monday: { a:1, b:2 },
    Tuesday: { c:3, d:4 }
    ...
  }

After:
  {
    Monday: { a:1, b:2, z:8 },
    Tuesday: { c:3, d:4 }
    ...
  }

db.foo.update({"_id" :ObjectId("...") },{$set : {"Monday.z":8}})

Insert a new field
https://stackoverflow.com/questions/26967525/insert-an-embedded-document-to-a-new-field-in-mongodb-document
db.test.update(
   { _id : 133 },
   { $set : { PackSizes:  {_id: 123, PackSizeName:"xyz", UnitName:"pqr"}} }
)
```

[**Update an array by index in a doc**](https://stackoverflow.com/questions/11372065/mongodb-how-do-i-update-a-single-subelement-in-an-array-referenced-by-the-inde)

```
Before:
  {
    _id : ...,
    other_stuff ... ,
    my_array : [
      { ... old content A ... },
      { ... old content B ... },
      { ... old content C ... }
    ]
  }

After:
  {
    _id : ...,
    other_stuff ... ,
    my_array : [
      { ... old content A ... },
      { ... NEW content B ... },
      { ... old content C ... }
    ]
  }

db["my_collection"].update(
    { "_id": ObjectId(document_id) },
    { "$set": { 'documents.'+str(doc_index)+'.content' : new_content_B}}
)
```

[**Distinct multiple keys**](https://stackoverflow.com/questions/11973725/how-to-efficiently-perform-distinct-with-multiple-keys)

```
use group

Ref:
 1. http://www.voidcn.com/article/p-trfewbcd-bbr.html
```

[**Distinct a list of sub-document field values**](https://stackoverflow.com/questions/16155266/mongodb-how-to-get-distinct-list-of-sub-document-field-values)

```
db.collection.distinct("children.child_name")
```



