# Loops

## while

## do while

## for

### Enhanced for loop / for-each loop

1. Enhanced for loop provides a simpler way to iterate through the elements of **a collection or array**. It is inflexible and should be used only when there is a need to iterate through the elements in sequential manner without knowing the index of currently processed element.

```text
for (T element:Collection obj/array)
{
    statement(s)
}

for (String x:array){}
```

#### [limitations](https://www.geeksforgeeks.org/for-each-loop-in-java/)

1. For-each loops are not appropriate when you want to modify the array
2. For-each loops do not keep track of index. So we can not obtain array index using For-Each loop
3. For-each only iterates forward over the array in single steps 只能类似i++这样traverse， 不能i--
4. For-each cannot process two decision making statements at once

#### Important points

1. Providing expression in for loop is must. A valid expression will lead to an infinite loop like while\(true\)
2. Multiple variables can be initialized in for loop, must be of the **same type**, only be used within loop
3. No redeclaration of a var

