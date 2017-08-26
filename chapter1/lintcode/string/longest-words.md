![](/assets/Screen Shot 2017-08-24 at 6.22.06 PM.png)
#Analysis
####Idea:
与length of last Word
1. 找到max length
2. 找到所有长为max length 的单词


```
class Solution {
    /**
     * @param dictionary: an array of strings
     * @return: an arraylist of strings
     */
    ArrayList<String> longestWords(String[] dictionary) {
        // write your code here
        int maxLen = 0;
        int dicLen = dictionary.length;
        ArrayList<String> ans = new ArrayList<String>(); //String[] ans = new String[dicLen] 错误点 什么是ArrayList
        // find the maximum length
        for (int i = 0; i < dicLen; i++) { //++i 与 i++区别？？？
            if (dictionary[i].length() > maxLen) {
                 maxLen = dictionary[i].length();
            }
        }
        // find all the words that have the maximum length
        for (int i = 0; i < dicLen; i++) {
            if (dictionary[i].length() == maxLen) {
                ans.add(dictionary[i]);
            }
        }
        return ans;
    }
};
```

