#####Idea:
1. 二分法
类似merge sort，每次将所有的list两两之间合并，直到所有list合并成一个。如果用迭代而非递归，则空间复杂度为O(1)。时间复杂度：
2n * k/2 + 4n * k/4 + ... + (2^x)n * k/(2^x) = nk * x
k/(2^x) = 1 -> 2^x = k -> x = log2(k)
所以时间复杂度为O(nk log(k))，与方法一相同。

#####Ref
[1.](http://blog.csdn.net/linhuanmars/article/details/19899259)
[2.](http://bangbingsyb.blogspot.com/2014/11/leetcode-merge-k-sorted-lists.html)

