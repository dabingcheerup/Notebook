![](/assets/Screen Shot 2017-08-29 at 3.52.46 PM.png)
#Analysis
####Idea:
1. Recursion类似Permutations，但是多传入一个参数pos用于记录位置，能加入的元素只能在pos和其之后的元素中寻找。同时，subsets长度可以任意，因此list在加入result时不用像permutation那样判断是否长度等于原数组长度。
2. Non-Recursion可以用位运算来实现。输入数组长度为n，则共有2^n个subset。从0到n－1位上，若用1表示取该位数，0表示不取该位数，则可以将这2^n种subset表示成0-2^n-1之间的二进制数。以[1,2,3]为例：
每次取一种subset的排列，看其在0-n－1位上的哪一位不为0，就将那一位上的数加入list。看第j位是否为0，可以和1 << j （j = 0, 1, ..., n-1）取&运算，若结果不为0，则第j位不为0。



```
// 递归：实现方式，一种实现DFS算法的一种方式
class Solution {
    /**
     * @param S: A set of numbers.
     * @return: A list of lists. All valid subsets.
     */
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> results = new ArrayList<>();
        
        if (nums == null) {
            return results;
        }
        
        if (nums.length == 0) {
            results.add(new ArrayList<Integer>());
            return results;
        }
        
        Arrays.sort(nums);
        helper(new ArrayList<Integer>(), nums, 0, results);
        return results;
    }
    
    
    // 递归三要素
    // 1. 递归的定义：在 Nums 中找到所有以 subset 开头的的集合，并放到 results
    private void helper(ArrayList<Integer> subset,
                        int[] nums,
                        int startIndex,
                        List<List<Integer>> results) {
        // 2. 递归的拆解
        // deep copy
        // results.add(subset);
        results.add(new ArrayList<Integer>(subset));
        
        for (int i = startIndex; i < nums.length; i++) {
            // [1] -> [1,2]
            subset.add(nums[i]);
            // 寻找所有以 [1,2] 开头的集合，并扔到 results
            helper(subset, nums, i + 1, results);
            // [1,2] -> [1]  回溯
            subset.remove(subset.size() - 1);
        }
        
        // 3. 递归的出口
        // return;
    }
}

// Non Recursion
class Solution {
    /**
     * @param S: A set of numbers.
     * @return: A list of lists. All valid subsets.
     */
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        int n = nums.length;
        Arrays.sort(nums);
        
        // 1 << n is 2^n
        // each subset equals to an binary integer between 0 .. 2^n - 1
        // 0 -> 000 -> []
        // 1 -> 001 -> [1]
        // 2 -> 010 -> [2]
        // ..
        // 7 -> 111 -> [1,2,3]
        for (int i = 0; i < (1 << n); i++) {
            List<Integer> subset = new ArrayList<Integer>();
            for (int j = 0; j < n; j++) {
                // check whether the jth digit in i's binary representation is 1
                if ((i & (1 << j)) != 0) {
                    subset.add(nums[j]);
                }
            }
            result.add(subset);
        }
        return result;
    }
}
```

