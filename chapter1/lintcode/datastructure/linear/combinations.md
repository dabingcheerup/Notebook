![](/assets/Screen Shot 2017-09-02 at 10.54.12 AM.png)

# Analysis

#### Idea:

与subset相似，backtracking的题，用排列组合模板  
Subsets  
题目：给定一个数组，没有重复数字。返回所有的子集。要求子集有序、子集间不重复。  
解法：回溯法。背包问题，每次选一个数字或者不选，同时step+1，直到step == s.size\(\)则保存结果并返回。  
Combinations  
题目：给定n，k，返回包含k个数字的1.....n的子集。  
解法：同上背包问题。每次选或者不选，同时step +1，只不过退出条件变成了 combine.size\(\) == k

```
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> list = new ArrayList<>();
    Arrays.sort(nums); //*
    backtrack(list, new ArrayList<>(), nums, 0);
    return list;
}

private void backtrack(List<List<Integer>> list , List<Integer> tempList, int [] nums, int start){
    list.add(new ArrayList<>(tempList));
    for(int i = start; i < nums.length; i++){
        tempList.add(nums[i]);
        backtrack(list, tempList, nums, i + 1);
        tempList.remove(tempList.size() - 1);
    }
}

public class Solution {
    /*
     * @param n: Given the range of numbers
     * @param k: Given the numbers of combinations
     * @return: All the combinations of k numbers out of 1..n
     */
    public List<List<Integer>> combine(int n, int k) {
        // write your code here
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        List<Integer> solution = new ArrayList<Integer>();
        helper(result, solution, n, k, 1); //*从1开始
        return result;
    }
    private void helper(List<List<Integer>> result, List<Integer> solution, int n, int k, int start) {
        // 输出的条件
        if (solution.size() == k) {
            result.add(new ArrayList<Integer>(solution)); //* <Integer>
            return; //*
        }
        for (int i = start; i <= n; i++) {
            solution.add(i);
            // the new start should be after the next number after i
            helper(result, solution, n, k, i + 1);
            solution.remove(solution.size() - 1);
        }
    }

}
```

![](/assets/Screen Shot 2017-09-02 at 11.27.57 AM.png)

