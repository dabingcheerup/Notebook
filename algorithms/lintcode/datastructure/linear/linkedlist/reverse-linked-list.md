# Reverse Linked List

![](../../../../../.gitbook/assets/screen-shot-2018-02-02-at-9.48.06-pm.png)

## 题目假设

## 重要问题

## 直觉

## 解决方法可行性

## 解决方案

## 数据结构

## 复杂度

## Code

```text
public ListNode reverse(ListNode head) {
    ListNode prev = null;
    while(head != null){
        ListNode temp = head.next;
        head.next = prev;
        prev = head;
        head = temp;
    }
    return prev;
}
```

