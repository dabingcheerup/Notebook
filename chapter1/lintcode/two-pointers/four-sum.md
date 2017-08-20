![](/assets/Screen Shot 2017-08-20 at 2.52.05 PM.png)
#Analysis
#### Idea:
1. for循环找a + b, index分别是i, j = i + 1
2. 用两指针left和right标记，在a、b后面找所有可能的c、d
3. 若 a + b + c + d = target, 返回； 若 < target，left++； 若 > target, right--; 直到left和right指针相遇，找到所有可能的c、d组合。随后由for循环更新a、b
4. 注意a、b、c和d 都要判断有无重复，重复的话跳过因为会产生相同结果