![](/assets/Screen Shot 2017-08-24 at 9.07.30 PM.png)
#Analysis
####Idea:
1. 又是一道数学题。判断是否是回文数字，只要将数字反转即可（和string tointeger类似）。但是这里其实不用考虑溢出的问题，因为给的是一个integer，如果是回文，则反转之后一定还是原来的integer，如果溢出则一定不会是回文。负数也不是回文。


```
public class Solution {
    /*
     * @param num: a positive number
     * @return: true if it's a palindrome or false
     */
    public boolean isPalindrome(int num) {
        // write your code here
        if (num < 0) {
            return false;
        } 
        int reverse =0;
        int temp = num;
        while (temp != 0) {
            reverse = reverse * 10 + temp % 10;
            temp /= 10;
        }
        return reverse == num;
    }
}
```

