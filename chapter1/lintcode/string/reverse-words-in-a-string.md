![](/assets/Screen Shot 2017-08-24 at 10.24.53 AM.png)
#Analysis
####Idea:
看上去有点象以前两次reverse的那道题，但这道题有所不同的地方就是需要处理空格。
1，要求删除开头和结尾的多余空格。
2，如果两个单词之间有多余空格的话，也要删除。

这样的话，就不能用两次reverse的方法了。


```
public class Solution {
    /*
     * @param s: A string
     * @return: A string
     */
    public String reverseWords(String s) {
        // write your code here
        if (s == null || s.length() == 0) {
            return "";
        }
        // 创建存储结果的string
        String[] array = s.split(" "); // 将字符按空格进行分割
        StringBuilder sb = new StringBuilder(); //????
        // 反向输出之前分割的字符串加到数组中
        for (int i = array.length - 1; i >= 0; --i) {
            if (!array[i].equals("")) {
                sb.append(array[i]).append(" ");
            }
        }
        // remove the last " "
        return sb.length() == 0 ? "" : sb.substring(0, sb.length() - 1); //?????
    }
}
```

![](/assets/Screen Shot 2017-08-24 at 10.47.59 AM.png)