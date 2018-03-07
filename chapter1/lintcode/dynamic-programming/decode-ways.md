![](/assets/Screen Shot 2018-03-07 at 4.54.43 PM.png)
#####Idea1:
类似climbing stairs, 用dp解决
从后往前读
1. n = s.length(); new int[n+1] dp
2. CC 考虑只有一个字符时：
    1. init dp[n] = 1
    2. 0无效，所以判断s.charAt(n-1)最后一个字符在这是唯一字符是否为0，若0，则dp[n-1]=0, or =1
3. 从第i=n-2字符开始，先判断当前第i字符是否为‘0’，是continue, 不是再判断Integer.paresInt(s.substring(i, i+2))的两位数是否<=26
    Y dp[i] = dp[i+1] + dp[i+2] //i+2相当于n,s不会overflow吗
    N dp[i] = dp[i+1]
######Code    


```
class Solution {
    public int numDecodings(String s) {
        int n = s.length();
        // CC: s is an empty string
        if(n == 0) return 0;
        
        //* init an int array to store #ways
        int[] dp = new int[n + 1];
        // init dp[n] = 1, bc n could be, there is only one char in s
        dp[n] = 1;
        //there is only one character in the string, if this character is not 0, there will be an answer, or there will be no answer.
        dp[n-1] = s.charAt(n-1) != '0'? 1 : 0;
        
        // start dp
        for(int i = n-2; i >= 0; i--) {
            //
            if(s.charAt(i) == '0') continue;
            else dp[i] = (Integer.parseInt(s.substring(i, i+2)) <= 26) ? dp[i+1] + dp[i+2] : dp[i+1];
        }
        return dp[0];
    }
}
```
#####Idea2
从前往后

```
 public class Solution {
    public int numDecodings(String s) {
        if(s == null || s.length() == 0) {
            return 0;
        }
        int n = s.length();
        int[] dp = new int[n+1];
        dp[0] = 1;
        dp[1] = s.charAt(0) != '0' ? 1 : 0;
        for(int i = 2; i <= n; i++) {
            int first = Integer.valueOf(s.substring(i-1, i));
            int second = Integer.valueOf(s.substring(i-2, i));
            if(first >= 1 && first <= 9) {
               dp[i] += dp[i-1];  
            }
            if(second >= 10 && second <= 26) {
                dp[i] += dp[i-2];
            }
        }
        return dp[n];
    }
}

```

