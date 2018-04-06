![](/assets/Screen Shot 2018-04-06 at 11.19.10 AM.png)

#####Idea
1. 记录frequency
2. for loop 从头traverse，找到出现次数为1的，返回其index
用int[]
String for loop 用到s.charAt(i)

#####Code


```
public int firstUniqChar(String s) {
        int[] freq = new int[26];
        
        for(char c : s.toCharArray()) {
            freq[c-'a']++;
        }
        for(int i = 0; i < s.length(); i++) {
            if(freq[s.charAt(i)-'a'] == 1) {
                return i;
            }
        }
        return -1;
    }
```

