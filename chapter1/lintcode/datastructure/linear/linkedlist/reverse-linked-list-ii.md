![](/assets/Screen Shot 2018-02-03 at 10.01.34 AM.png)
#####题目假设
1. Reverse a linked list from position m to n

#####重要问题
1. get to pos m
2. reverse the list from m to n


#####直觉
1. traverse linked list to get to pos m
2. 4 steps reverse

#####解决方法可行性
1. cc: head == null, return null

#####解决方案
1. dummy marks the head of list, finally return dummy.next
2. prev initialized dummy.next, _for loop 到是第m-1个node_，然后prev是一直不变的，总是指向表头
3. end 是第m个node，_从m到n反转_，所以它也是list的最后一个。end.next是当前要被插到表头的
    4. cur 是end.next,当前要被插入的node，把cur拎出来，让end表尾指向cur.next
    5. cur成为表头：
        cur指向原表头，即cur.next = prev.next
        prev永远指向表头，所以表头更新了，它也要指向新表头，prev.next = cur
    6. 更新cur为下一个当前要被Reverse的node，即end.next
    
**找到prev（指向表头）和end（标记表尾和找cur）后它们就不变，变的是表头，找end.next为cur成为新表头**

#####数据结构
1. linked list, dummy node

#####复杂度
#####Code


```
 public ListNode reverseBetween(ListNode head, int m, int n) {
        // cc
        if(m > n || head == null) return null;
        
        ListNode dummy = new ListNode(0);   // create a dummy node to mark the head of this list
        dummy.next = head;
        ListNode prev = dummy;  // make a pointer pre as a marker for the node before reversing
         
        //get to pos points to m
        for(int i = 0; i < m-1; i++){
            prev = prev.next;
        }
        
        //reverse from m to n
        ListNode end = prev.next;   // end is the last node of reversed linked list
        ListNode cur = end.next;    // cur is end.next, which is the current one that need to be reversed
        
        for(int i = 0; i < n-m; i++){
            end.next = cur.next;    //seperate the cur, end.next becomes cur.next
            cur.next = prev.next;   //cur should point to the first node of reversed list, which is prev.next
            prev.next = cur;    //prev.next is the first node of reversed list, so update prev.next as cur  
            cur = end.next;   //update cur as the next node need to be reversed, which is end.next
            
        }
        return dummy.next;
    }
```



