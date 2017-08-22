![](/assets/Screen Shot 2017-08-21 at 4.28.39 PM.png)
# Analysis
#### Idea:
1. 快慢指针，相遇的话就是有环
2. 注意要判断fast指针有没有先到底


```
/**
 * Definition for ListNode.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int val) {
 *         this.val = val;
 *         this.next = null;
 *     }
 * }
 */ 
public class Solution {
    /**
     * @param head: The first node of linked list.
     * @return: True if it has a cycle, or false
     */
    public boolean hasCycle(ListNode head) {  
        // write your code here
        //快慢指针，相遇的话就有环
        if (head == null || head.next == null) {
            return false;
        }
        // Initialize fast slow
        ListNode fast, slow;
        fast = head.next;
        slow = head;
        while (fast != slow) {
            if (fast == null || fast.next == null) { //如果没有环，可确定是否到底
                return false;
            }
            fast = fast.next.next;
            slow = slow.next;
        }
        return true;
    }
}```

