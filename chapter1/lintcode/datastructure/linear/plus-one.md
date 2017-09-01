![](/assets/Screen Shot 2017-08-31 at 9.20.15 PM.png)
#Analysis
总结下涉及到进位的题，包括十进制，二进制等
1. 每一位取出之后加上之前一位的进位，%10之后为该位的数字，/10之后为该位的进位。有几点注意：
    1) 若前一位的进位为0，可以直接停止循环
    2) 若最左边一位的进位为0可以直接返回，否则要用一个长度加1的新数组的第一位保存1，其它各位与原数组相同
    3) 时间复杂度是O(1)


```
public class Solution {
    // The complexity is O(1)
    // f(n) = 9/10 + 1/10 * O(n-1)
    //  ==>  O(n) =  10 / 9 = 1.1111 = O(1)
    
    public int[] plusOne(int[] digits) {
        int carries = 1;
        for(int i = digits.length-1; i>=0 && carries > 0; i--){  // fast break when carries equals zero
            int sum = digits[i] + carries;
            digits[i] = sum % 10;
            carries = sum / 10;
        }
        if(carries == 0)
            return digits;
            
        int[] rst = new int[digits.length+1];
        rst[0] = 1;
        for(int i=1; i< rst.length; i++){
            rst[i] = digits[i-1];
        }
        return rst;
    }
}


```


