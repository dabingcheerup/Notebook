![](/assets/Screen Shot 2018-03-08 at 4.41.20 PM.png)
#####Idea
要O(n)，就想到用HashMap记录每个consecutive subsequence's boundaries, 在这个过程中update maxLen
#####Code

```
 public int longestConsecutive(int[] nums) {
        int maxLen = 0;
        //Hashmap
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        //find consecutive boundries by n-1 and n+1
        for(int n : nums) {
            if(!map.containsKey(n)) {
                int left = (map.containsKey(n-1))? map.get(n-1) : 0;
                int right = (map.containsKey(n+1))? map.get(n+1) : 0;
                
                // sum: length of the sequence that n is in
                int sum = left + right + 1;
                // put the pair (n, the update length of its sequence)
                map.put(n, sum);
                //update maxLen
                maxLen = Math.max(maxLen, sum);
                //the boundary of the sequence if n-left and n-right, update their values in map as maxLen
                map.put(n-left, sum);
                map.put(n+right, sum);
                
            } else {
                //skip duplicates
                continue;
            }
        }
        return maxLen;
    }
```

#####Syntax
HashMap
1. map.containsKey()
2. map.put(key, value)
3. map.get(key) get key's value