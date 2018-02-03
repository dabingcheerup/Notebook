Definition for singly-linked list.
 
```
 public class ListNode {
      int val;
      ListNode next;
      ListNode(int x) {
          val = x;
          next = null;      
      }
  }
``` 
Constructor:
ListNode head = new ListNode(val)

Methods:
1. list.add(val)
2. list.addFirst() / list .addLast()

Traverse:
```
while(head != null){
    head = head.next;
}
```


