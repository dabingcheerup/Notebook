![](/assets/Screen Shot 2018-03-02 at 4.05.27 PM.png)

#####Idea:
考虑三个方面：

1. n == 0, return 1
2. 要考虑n < 0，那么n = -n; x = 1/x;
3. 根据n的奇偶情况来递归求值

    1. 偶数，则递归myPow(x*x, n/2)
    2. 奇数，则递归x*myPow(x*x, n/2)


```
public class Solution {
    public double pow(double x, int n) {
        if(n == 0)
            return 1;
        if(n<0){
            n = -n;
            x = 1/x;
        }
        return (n%2 == 0) ? pow(x*x, n/2) : x*pow(x*x, n/2); //n为奇数时
    }
}
```



