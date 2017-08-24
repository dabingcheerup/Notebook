![](/assets/Screen Shot 2017-08-23 at 8.22.33 PM.png)
#Analysis
####Idea:
1. 方法一：将两个数转换成二进制整数，然后用位运算进行相加，再将所得结果用二进制string表示。
2. 方法二：将长的那个数放在前，短的数放在后。用carriers记录进位。然后从后往前将两个数对应的位置上的数相加上carriers，将结果%2加入res之前，同时用结果/2来更新carriers。当短的数到头之后，则只要将长的数的位上的数和carriers相加即可。最后当长的数也到头之后，若carriers为1，则在res前加"1"即可。

