![](/assets/Screen Shot 2017-08-20 at 2.52.05 PM.png)

# Analysis

#### Idea:

1. 两个for loop找a + b的组合, index分别是i, j = i + 1，注意**跳过a, b的重复**
2. 用两指针left和right标记，在a、b后面找所有可能的c、d
3. 若 a + b + c + d = target, 返回； 若 < target，left++； 若 > target, right--; 直到left和right指针相遇，找到所有可能的c、d组合。随后由for循环更新a、b
4. 注意a、b、c和d 都要判断有无重复，重复的话跳过因为会产生相同结果

#### Solution

```
public List<List<Integer>> fourSum(int[] nums, int target) {
       List<List<Integer>> res = new LinkedList<>();
		Arrays.sort(nums);
		int sum;
		for(int i = 0; i < nums.length-3; i++) {
			if(i!=0 && (nums[i] == nums[i-1])) continue;
			for(int j = i+1; j < nums.length-2; j++) {
			    if(j != i+1 && (nums[j] == nums[j-1])) continue;
				int low = j + 1, high = nums.length -1;
				while(low < high) {
					sum = nums[i] + nums[j] + nums[low] + nums[high];
					if(sum == target) {
						res.add(Arrays.asList(nums[i], nums[j], nums[low], nums[high]));
						low++;
						high--;
						while(low < high && nums[low] == nums[low-1]) low++;
						while(low < high && nums[high] == nums[high+1]) high--;
					}else if(sum < target) {
						low++;
					}else {
						high--;
					}
				}
			}
		}
		return res;
    }
```

#### 知识点：

1. skip duplicate 看是否与前一个元素相同，相同的continue 或者相应的其他操作



