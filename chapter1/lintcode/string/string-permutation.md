![](/assets/Screen Shot 2017-08-26 at 10.18.34 AM.png)
#Analysis
####Idea:
基本与two strings are anagram一样
1. 数组记录A出现的字符
2. 和B出现的字符消除，如果出现负数则不同


```
public class Solution {
    /*
     * @param A: a string
     * @param B: a string
     * @return: a boolean
     */
    public boolean Permutation(String A, String B) {
        // write your code here
        if (A.length() != B.length()) {
            return false;
        }
        int[] count = new int[256];
        // 遍历A
        for (int i = 0; i < A.length(); i++) {
            count[(int) A.charAt(i)]++;
        }
        // 遍历B
        for (int i = 0; i < B.length(); i++) {
            count[(int) B.charAt(i)]--;
            if (count[(int) B.charAt(i)] < 0) {
                return false;
            }
        }
        return true;
    }
}
```
![](/assets/Screen Shot 2017-08-26 at 10.23.03 AM.png)

