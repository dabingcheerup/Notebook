![](/assets/Screen Shot 2018-02-04 at 2.14.58 PM.png)
#####题目假设
1. a sorted array is rotated at some pivot
2. given a target, find its index, no duplicate

#####idea
1. 考虑cc
2. initialize start, end
3. while(start+1 < end)
    初始化mid
    i. A[mid]== target, return mid
    ii. 判断mid在哪条线上：
        if: A[start] < target(在1线上)
            类似template的步骤
            
        else：（在2线上）

4. 最后target和start、end比较找到index，没找到return -1    

#####Code


```
public int search(int[] A, int target) {
        if (A == null || A.length == 0) {
            return -1;
        }

        int start = 0;
        int end = A.length - 1;
        int mid;
        
        while (start + 1 < end) {
            mid = start + (end - start) / 2;
            if (A[mid] == target) {
                return mid;
            }
            if (A[start] < A[mid]) {
                // situation 1, red line
                if (A[start] <= target && target <= A[mid]) {
                    end = mid;
                } else {
                    start = mid;
                }
            } else {
                // situation 2, green line
                if (A[mid] <= target && target <= A[end]) {
                    start = mid;
                } else {
                    end = mid;
                }
            }
        } // while
        
        if (A[start] == target) {
            return start;
        }
        if (A[end] == target) {
            return end;
        }
        return -1;
    }
    
```

