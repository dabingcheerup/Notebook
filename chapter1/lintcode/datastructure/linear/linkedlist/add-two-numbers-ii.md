![](/assets/Screen Shot 2018-02-02 at 4.48.37 PM.png)

#####题目假设
1. the digits are stored in forward order, return the sum as linkedList

#####重要问题
1. 从list尾开始加两个数，所以要倒着取两个list的结点，用stack
2. 怎么加，怎么存进位，怎么存sum%10

#####直觉
1. traverse l1, l2, push each listNode into stack s1, s2
2. if s1 != null, pop out the top node, then add to sum. so as s2.
3. listNode dummy = new listNode(0)

#####解决方法可行性

#####解决方案
1. Initialize: new 一个dummyNode
2. 每次计算时(while(s1 != null || s2 != null))  
    2.1. 把sum%10存放在dummy中，即当前LinkedList的表头
    2.2. new一个ListNode head存放进位sum/10
    2.3. head.next = dummy
    2.4. dummy = head 更新dummy，让它作为当前LinkedList的表头
    2.5. sum /= 10作为进位，用于下次的计算

#####数据结构
1. stack
2. linkedlist dummyNode

#####复杂度
1. 