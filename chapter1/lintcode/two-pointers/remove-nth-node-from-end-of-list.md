![](/assets/Screen Shot 2017-08-22 at 9.18.50 PM.png)
#Analysis
####Idea:
目标： 就是找到从后往前数第n个数删除
方法1： 反转list后 找第n个删除
方法2： 不用长度，而利用公式算出n的位置 two pointer
1. 如果只能走一趟，那可以用two pointer。总体思想为：要删去从后往前第n个元素，即删去从前往后第size-n+1个元素。一个指针先从前往后走n步，然后此时从n到list尾部（null）的距离为size-n+1，这时候另一个指针从dummy（第一个元素之前的元素）和第一个指针一起往后移动直到第一个指针到达list尾部为止，此时第二个指针到达第size-n个元素，只要删去其后面的元素即可。


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
     * @param n: An integer.
     * @return: The head of linked list.
     */
    ListNode removeNthFromEnd(ListNode head, int n) {
        // write your code here
        if (n <= 0) {
            return null;
        }
        ListNode dummy = new ListNode(0);
        dummy.next = head; //存head
        ListNode preDelete = dummy;
        for (int i = 0; i < n; i++) {
            if (head == null) {
                return null;
            }
            head = head.next; //挪动指针
        }
        while (head != null) {
            head = head.next;
            preDelete = preDelete.next;
        }
        preDelete.next = preDelete.next.next; // 删除了preDelete.next
        return dummy.next;
    }
}

```
#### 知识点
1. Linked List 的题基本考虑到用dummyNode
2. 挪动指针 head = head.next  删除指针 

