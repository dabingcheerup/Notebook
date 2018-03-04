![](/assets/Screen Shot 2018-03-04 at 2.01.45 PM.png)
#####Idea
1. 每一行确定可以放的n个单词，满足n个单词长+(n-1) < L
2. 若确定则单词间的空格要平均分，总空格数= L-n个单词长，均空格数 = 总空格数/(n-1)
    若不能均分总空格数，使最左边的空格数最多，即加上余数
3. CC 最后一行若只有一个单词要左顶

#####Ref
1. [Text Justification 解题报告](http://blog.csdn.net/ljiabin/article/details/44976999)
