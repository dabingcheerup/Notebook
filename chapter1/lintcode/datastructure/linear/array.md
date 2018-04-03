

#####Arrays Class


```
1. declare Array variables
dataType[] arrayRefVar;    //int[] arr; char[] charArr...

2. create Array
arrayRefVar = new dataType[arraySize];

3. for each
for (dataType element: arrayRefVar)

4. arr.length

5. Arrays.sort(arr)

```

#####Treemap
1. HashMap不保证数据有序，LinkedHashMap保证数据可以保持插入顺序, Map可以**保持key的大小顺序**的时候，我们就需要利用**TreeMap**了


```
1. K ceilingKey(K key)
This method returns the least key greater than or equal to the given key, or null if there is no such key.

2. K floorKey(K key)
This method returns the greatest key less than or equal to the given key, or null if there is no such key.
```


######Ref
[TreeMap](http://wiki.jikexueyuan.com/project/java-enhancement/java-twentyseven.html)
