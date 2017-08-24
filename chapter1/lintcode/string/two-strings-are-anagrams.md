![](/assets/Screen Shot 2017-08-24 at 11.05.00 AM.png)
#Analysis
####Idea:
与Unique characters相似
1. 先判断两字符串长度相同 
2. 两个for，第一个遍历s, 用int[]记录s中出现的字符，再遍历t, 出现的字符count--，相当于抵消。 如果count < 0证明不一样
3. 注意数组中字符的标记是把字符转换为int类型作为index


```
public class Solution {
    /**
     * @param s: The first string
     * @param b: The second string
     * @return true or false
     */
    public boolean anagram(String s, String t) {
        // write your code here
        if (s.length() != t.length()) {
            return false;
        }
        // 像reverse words 那道题 256长记录出现过的字符，不同的是要记录每个字符出现的次数
        int[] count = new int[256];
        // 先遍历s
        for (int i = 0; i < s.length(); i++) {
            count[(int) s.charAt(i)]++;
        }
        // 遍历t
        for (int i = 0; i < t.length(); i++) {
            count[(int) t.charAt(i)]--; // 抵消之前出现过的s字符
            if (count[(int) t.charAt(i)] < 0) {
                return false;
            }
        }
        return true;
     }
};
```
####知识点：
1. count[(int) s.charAt(i)]
![](/assets/Screen Shot 2017-08-24 at 11.28.28 AM.png)

















































