![](/assets/Screen Shot 2017-08-22 at 10.48.06 AM.png)

# Analysis

#### Idea:
1. 从head开始直到head为null，用两个表尾node Gtail和Ltail分别存放找到的<=x 和 >x的ListNode，最后把两个LinkedList结合在一起，并把第二个LinkedList的尾指向null，避免cycle和错误

#### 难点：
1. **要4个node！** 要用两个dummyNode记录greater和less的表头，另两个node是记录它们的表尾Gtail和Ltail，以便扩充表。

1. 对linked list结构不熟，不知道怎么交换两个元素，array交换简单，用三个变量【用dummynode**复习点**】



```
public ListNode partition(ListNode head, int x) {
     
        ListNode greaterDummy = new ListNode(0);
        ListNode lessDummy = new ListNode(0);
        ListNode gTail = greaterDummy, lTail = lessDummy;
        while(head != null) {
           if(head.val < x) {
               less.next = head;
               less = less.next;
           }else {
               greaterEqual.next = head;
               greaterEqual = greaterEqual.next;
           }
           head = head.next; 
        }
        greaterEqual.next = null;
        less.next = greaterDummy.next;
        return lessDummy.next;
    }
```




