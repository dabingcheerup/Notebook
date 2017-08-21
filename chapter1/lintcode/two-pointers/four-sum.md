![](/assets/Screen Shot 2017-08-20 at 2.52.05 PM.png)
#Analysis
#### Idea:
1. for循环找a + b, index分别是i, j = i + 1
2. 用两指针left和right标记，在a、b后面找所有可能的c、d
3. 若 a + b + c + d = target, 返回； 若 < target，left++； 若 > target, right--; 直到left和right指针相遇，找到所有可能的c、d组合。随后由for循环更新a、b
4. 注意a、b、c和d 都要判断有无重复，重复的话跳过因为会产生相同结果
#### Solution


```
public class Solution {
    /*
     * @param numbers: Give an array
     * @param target: An integer
     * @return: Find all unique quadruplets in the array which gives the sum of zero
     */
    public List<List<Integer>> fourSum(int[] numbers, int target) {
        // write your code here
        // results stores all unique quardruplets
        List<List<Integer>> results = new ArrayList<List<Integer>>();
        // sort numbers
        Arrays.sort(numbers);
        for (int i = 0; i < numbers.length -3; i++) {
            // skip duplicates
            if (i != 0 && numbers[i] == numbers[i - 1]) {
                continue;
            }
            //
            for (int j = i + 1; j < numbers.length - 2; j++) {
                if (j != i + 1 && numbers[j] == numbers[j - 1]) {
                    continue;
                }
                int left = j + 1;
                int right = numbers.length - 1;
                while (left < right) {
                    int sum = numbers[i] + numbers[j] + numbers[left] + numbers[right];
                    if (sum < target) {
                        left++;
                    } else if (sum > target) {
                        right--;
                    } else {
                        ArrayList<Integer> tmp = new ArrayList<Integer>();
                        tmp.add(numbers[i]);
                        tmp.add(numbers[j]);
                        tmp.add(numbers[left]);
                        tmp.add(numbers[right]);
                        results.add(tmp);
                        left++;
                        right--;
                        //skip duplicates
                        while (left < right && numbers[left] == numbers[left -1]) {
                            left++;
                        }
                        while (left < right && numbers[right] == numbers[right + 1]) {
                            right--;
                        }
                    }
                }
            }
        }
        return results;
    }
};public class Solution {
    /*
     * @param numbers: Give an array
     * @param target: An integer
     * @return: Find all unique quadruplets in the array which gives the sum of zero
     */
    public List<List<Integer>> fourSum(int[] numbers, int target) {
        // write your code here
        // results stores all unique quardruplets
        List<List<Integer>> results = new ArrayList<List<Integer>>();
        // sort numbers
        Arrays.sort(numbers);
        for (int i = 0; i < numbers.length -3; i++) {
            // skip duplicates
            if (i != 0 && numbers[i] == numbers[i - 1]) {
                continue;
            }
            //
            for (int j = i + 1; j < numbers.length - 2; j++) {
                if (j != i + 1 && numbers[j] == numbers[j - 1]) {
                    continue;
                }
                int left = j + 1;
                int right = numbers.length - 1;
                while (left < right) {
                    int sum = numbers[i] + numbers[j] + numbers[left] + numbers[right];
                    if (sum < target) {
                        left++;
                    } else if (sum > target) {
                        right--;
                    } else {
                        ArrayList<Integer> tmp = new ArrayList<Integer>();
                        tmp.add(numbers[i]);
                        tmp.add(numbers[j]);
                        tmp.add(numbers[left]);
                        tmp.add(numbers[right]);
                        results.add(tmp);
                        left++;
                        right--;
                        //skip duplicates
                        while (left < right && numbers[left] == numbers[left -1]) {
                            left++;
                        }
                        while (left < right && numbers[right] == numbers[right + 1]) {
                            right--;
                        }
                    }
                }
            }
        }
        return results;
    }
};
```
#### 知识点：
1. skip duplicate 看是否与前一个元素相同，相同的continue 或者相应的其他操作

