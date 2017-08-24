![](/assets/Screen Shot 2017-08-24 at 11.31.59 AM.png)
#Analysis
####Idea:
1. 就是把计算过程code出来


```
public class Solution {
    /*
     * @param n: the nth
     * @return: the nth sequence
     */
    public String countAndSay(int n) {
        // write your code here
        // Initialize the beginning string
        String oldString = "1";
        // 求第n个
        while (--n > 0) {
            // stringbuilder 创建新字符串
            StringBuilder sb = new StringBuilder();
            char [] oldChars = oldString.toCharArray(); //????
            for (int i = 0; i < oldChars.length; i++) {
                int count = 1;
                //继续统计该数字的个数
                while((i + 1) < oldChars.length && oldChars[i] == oldChars[i + 1]) {
                    count++;
                    i++;
                }
                sb.append(String.valueOf(count) + String.valueOf(oldChars[i]));
            }
            oldString = sb.toString();
        }
        return oldString;
        
    }
}
```
####知识点：
1. StringBuilder 创建字符串  sb.toString()
2. String.toCharArray()
3. String.valueOf()


