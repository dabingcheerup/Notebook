![](/assets/Screen Shot 2017-08-24 at 6.03.21 PM.png)
#Analysis
####Idea:
1. 用split去掉空格，找到最后一个求其长度


```
public class Solution {
    /*
     * @param s: A string
     * @return: the length of last word
     */
    public int lengthOfLastWord(String s) {
        // write your code here
        if (s == null || s.length() == 0) {
            return 0;
        }
        // 
        String[] array = s.split(" ");
        int index = array.length - 1;
        String lastWord = array[index];
        int res = lastWord.length();
        return res;
    }
}
```
####知识点：
1. String[] array = s.split(" ")


