![](/assets/Screen Shot 2017-08-24 at 10.48.58 AM.png)
#Analysis
####Idea:
1. 不用其他data structure， 用一个256的boolean set初始化都为false，遍历str,标记所有出现过的字符true。如果碰到true就证明出现过了 直接return false


```
public class Solution {
    /**
     * @param str: a string
     * @return: a boolean
     */
    public boolean isUnique(String str) {
        // write your code here
        boolean[] char_set = new boolean[256]; //????
        for (int i = 0; i < str.length(); i++) {
            int val = str.charAt(i);
            if (char_set[val]){
                return false;
            } else {
                char_set[val] = true;
            }
        }
        return true;
    }
}
```
![](/assets/Screen Shot 2017-08-24 at 11.03.39 AM.png)
####知识点：
1. boolean[]

