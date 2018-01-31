![](/assets/Screen Shot 2017-08-20 at 9.58.30 AM.png)

# Analysis

#### 解题思路：

1. 找所有3pair，一个for循环固定第一个数用i标记index，赋两个指针left = i+1、right = numbers.length - 1，找剩下的两个数。如果这三个数的和与target的绝对差最小，暂时记为bestSum。 
2. 继续移动指针找其他两个数的组合。如果sum &lt; target, left++； 如果sum &gt; target, right--

```
public class Solution {
    /*
     * @param numbers: Give an array numbers of n integer
     * @param target: An integer
     * @return: return the sum of the three integers, the sum closest target.
     */
    public int threeSumClosest(int[] numbers, int target) {
        // write your code here
        if (numbers == null || numbers.length < 3) {
            return -1;
        }
        // sort numbers
        Arrays.sort(numbers);
        // bestSum stores the sum that is closest to the target
        // Initialize bestSum equals to the sum of first three elements
        int bestSum = numbers[0] + numbers[1] + numbers[2];
        // traverse all 3pairs, compare their sum to find which is bestSum
        for (int i = 0; i < numbers.length; i++) {
            // two pointer
            int left = i + 1, right = numbers.length - 1;
            while (left < right) { // when left and right pointer meets, stop searching
                // sum temperaly stores current 3pair 
                int sum = numbers[i] + numbers[left] + numbers[right];
                // bestSum and sum, which is closest to the target. absulote value
                if (Math.abs(target - sum) < Math.abs(target - bestSum)) {
                    bestSum = sum;
                }
                // continue to find next 3pair by moving pointers
                if (sum < target) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        return bestSum;
    }
};
```

#### 知识点

1. 绝对值 Math.abs\(\)
2. Array排序 Arrays.sort\(\)



