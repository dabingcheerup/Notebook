![](/assets/Screen Shot 2017-08-29 at 3.21.00 PM.png)
#Analysis
####Idea:
1. 在求n-1位数到n位数的时候，先求n-2位数到n-1位数，就如同下面一样：
![](https://zhengyang2015.gitbooks.io/lintcode/648870-20151107121324680-1898810728.png)
递归求解n时，可以对n－1位置上的数从0-9遍历，依次类推直到最后一位。


```
public class Solution {
    /**
     * @param n: An integer.
     * return : An array storing 1 to the largest number with n digits.
     */
    public List<Integer> numbersByRecursion(int n) {
        // write your code here
        List<Integer> res = new ArrayList<Integer>();
        if(n < 1){
            return res;
        }

        helper(n, 0, res);
        return res;
    }

    //ans在这里可以看成前一位的值，在递归过程中会乘以n－1次10，即10^(n-1)
    private void helper(int n, int ans, List<Integer> res){
        if(n==0){    // 1 ~9
            if(ans>0){
                res.add(ans);
            }
            return;
        }

        int i;
        for(i=0; i<=9; i++){
            helper(n-1, ans*10+i, res);
        }
    }
}
```
####知识点：
1. 为什么int i要放在for外面？

