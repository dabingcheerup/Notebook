##### ![](/assets/Screen Shot 2018-02-04 at 4.34.34 PM.png)

##### Idea

1. reverse\(\) 反转函数
2. rotate\(\) 中调用三次反转函数
3. k steps 有可能大于num.length
    所以 k = k % num.length

##### Code

```
 private void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++; end--;
        }
    }
    public void rotate(int[] nums, int k) {
        if (nums.length == 0) {
            return;
        }

        k = k % nums.length;
        reverse(nums, 0, nums.length - k - 1);
        reverse(nums, nums.length - k, nums.length - 1);
        reverse(nums, 0, nums.length - 1);
    }
```



