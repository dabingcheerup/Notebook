![](/assets/Screen Shot 2018-03-08 at 11.05.12 AM.png)
#####Idea
To find so far min price. init minPrice = prices[0]
1. traverse prices
if prices[i] > minPrice, we can sell it, update maxProfit = Math.max(maxProfit, prices[i] - minPrice)
else, we update minPrice = prices[i], we can buy at this lower price.

Notes:
1. CC: prices.length == 0

#####Code


```
public int maxProfit(int[] prices) {
        if(prices.length == 0) return 0;
        //init minimum price
        int minPrice = prices[0];
        int maxProfit = 0;
        // traverse to find maxPofit
        for(int i = 1; i < prices.length; i++) {
            // can sell it, then update the maxProfit
            if(prices[i] > minPrice) {
                maxProfit = Math.max(maxProfit, prices[i] - minPrice);
            } else {
                minPrice = prices[i];
            }
        }
        return maxProfit;
    }
```


