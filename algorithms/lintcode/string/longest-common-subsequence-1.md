# longest common subsequence

![](../../../.gitbook/assets/screen-shot-2017-08-26-at-1.53.14-pm.png)

## Analysis

### Idea:

与longest common substring相似 1. 用DP

```text
public class Solution {
    /*
     * @param A: A string
     * @param B: A string
     * @return: The length of longest common subsequence of A and B
     */
    public int longestCommonSubsequence(String A, String B) {
        // write your code here
        int n = A.length();
        int m = B.length();
        int f[][] = new int[n + 1][m + 1];
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= m; j++) {
                f[i][j] = Math.max(f[i - 1][j], f[i][j - 1]);
                if (A.charAt(i - 1) == B.charAt(j - 1)) {
                    f[i][j] =f[i - 1][j - 1] + 1;
                }
            }
        }
        return f[n][m];
    }
}
```

![](../../../.gitbook/assets/screen-shot-2017-08-26-at-1.55.04-pm.png)

