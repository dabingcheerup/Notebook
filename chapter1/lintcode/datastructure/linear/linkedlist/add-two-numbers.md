![](/assets/Screen Shot 2018-02-01 at 10.56.22 AM.png)

#####idea:
1. 反过来的加法过程
2. 注意：l1 和 l2 长度不同
    1. l1 == null && l2 == null
    2. l1 != null && l2 != null
    3. l1 != null
    4. l2 != null
    5. l1, l2 == null, carry > 0，新加一个node存放最高位的进位

#####题目假设
1. Two LinkedLists, l1 and l2 represent two numbers
2. digits are stored in reverse order, adds the two numbers and return the sum as a linked list in reverse order

#####重要问题
1. 进位
2. l1, l2的长度不同

#####直觉
1. traverse l1 和 l2

#####解决方法可行性
1. 根据l1,l2的情况分别处理

#####解决方案
1. l1 == null && l2 == null, return null
2. l1 != null && l2 != null, sum = l1.val + l2.val + carry
3. l1 != null, sum = l1.val + carry
4. l2 != null, sum = l2.val + carry
5. l1, l2 == null, carry > 0，新加一个node存放最高位的进位

#####数据结构
1. LinkedList DummyNode
#####复杂度
1. while loop, O(n)

#####Code

```

/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        if(l1 == null && l2 == null) {
            return null;
        }
            
        ListNode head = new ListNode(0);
        ListNode point = head;
        int carry = 0;
        while(l1 != null && l2!=null){
            int sum = carry + l1.val + l2.val;
            point.next = new ListNode(sum % 10);
            carry = sum / 10;
            l1 = l1.next;
            l2 = l2.next;
            point = point.next;
        }
        
        while(l1 != null) {
            int sum =  carry + l1.val;
            point.next = new ListNode(sum % 10);
            carry = sum /10;
            l1 = l1.next;
            point = point.next;
        }
        
        while(l2 != null) {
            int sum =  carry + l2.val;
            point.next = new ListNode(sum % 10);
            carry = sum /10;
            l2 = l2.next;
            point = point.next;
        }
        
        if (carry != 0) {
            point.next = new ListNode(carry);
        }
        return head.next;
    }
}

```



```
// version: 高频题班
public class Solution {
    /**
     * @param l1: the first list
     * @param l2: the second list
     * @return: the sum list of l1 and l2
     */
    public ListNode addLists(ListNode l1, ListNode l2) {
        // write your code here
        ListNode dummy = new ListNode(0);
        ListNode tail = dummy;

        int carry = 0;
        for (ListNode i = l1, j = l2; i != null || j != null; ) {
            int sum = carry;
            sum += (i != null) ? i.val : 0;
            sum += (j != null) ? j.val : 0;

            tail.next = new ListNode(sum % 10);
            tail = tail.next;

            carry = sum / 10;
            i = (i == null) ? i : i.next;
            j = (j == null) ? j : j.next;
        }

        if (carry != 0) {
            tail.next = new ListNode(carry);
        }
        return dummy.next;
    }
}
```


