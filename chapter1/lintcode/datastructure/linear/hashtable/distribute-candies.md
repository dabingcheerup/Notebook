![](/assets/Screen Shot 2018-04-05 at 11.05.16 PM.png)
#####Idea
HashSet找出candies的种类

#####Code


```
 public int distributeCandies(int[] candies) {
        int n = candies.length;
        Set<Integer> distinct = new HashSet<>();
        for(int c : candies) distinct.add(c);
        return distinct.size() >= n/2 ? n/2 : distinct.size();
    }
```

