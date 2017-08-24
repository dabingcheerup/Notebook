![](/assets/Screen Shot 2017-08-23 at 9.13.05 PM.png)
#Analysis
####Idea:
1. 先create一个26长的数组，遍历A，标记出现的字母
2. 与B的字母比较，找到一个-1，如果<0 证明之前的是0 A中没有在这个字母


```
public class Solution {
    /*
     * @param A: A string
     * @param B: A string
     * @return: if string A contains all of the characters in B return true else return false
     */
    public boolean compareStrings(String A, String B) {
        // write your code here
        // 用长度为26的数组记录A所包含的字母
        int[] counts = new int[26];
        // 先初始化
        for (int i = 0; i < 26; i++) {
            counts[i] = 0;
        }
        // 遍历A
        for (int i = 0; i < A.length(); i++) {
            counts[A.charAt(i) - 'A']++; //??
        }
        for (int i = 0; i < B.length(); i++) {
            counts[B.charAt(i) - 'A']--;
            if (counts[B.charAt(i) - 'A'] < 0) {
                return false;
            }
        }
        return true;
    }
}
```
####知识点
1. counts[A.charAt(i) - 'A'] 不懂 -A什么意思

![](/assets/Screen Shot 2017-08-23 at 9.17.12 PM.png)

