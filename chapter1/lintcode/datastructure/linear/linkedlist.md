Definition for singly-linked list.

```
 public class ListNode {
      int val;
      ListNode next;
      // Constructor
      ListNode(int x) {
          val = x;
          next = null;      
      }
  }
```

Constructor:  
ListNode head = new ListNode\(val\)

Methods:  
1. list.add\(val\),list.addFirst\(\) / list .addLast\(\)  
2. [list.get\(int index\)](https://www.geeksforgeeks.org/java-util-linkedlist-get-getfirst-getlast-java/), return the element at the specified position in this list  
Traverse:

```
while(head != null){
    head = head.next;
}
```

[Priority queue](https://my.oschina.net/leejun2005/blog/135085)

