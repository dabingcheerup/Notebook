#####Idea:
要考虑：
1. 正负数；用个boolean negative 表示结果应该是正数或负数
2. dividend为0
3. 因为输入的都是int型，比如被除数是-2147483648，在int范围内，当除数是-1时，结果就超出了int范围，需要返回INT_MAX
解法：
1. Brute force: while dividend >= divisor, dividend不断减去divisor, 减去的次数为商，假设为n,则O(n)
2. 

Sytax
1. Integer.MAX_VALUE
2. Integer.MIN_VALUE