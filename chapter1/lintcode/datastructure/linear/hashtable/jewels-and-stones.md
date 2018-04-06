![](/assets/Screen Shot 2018-04-05 at 10.34.56 PM.png)

#####Idea
1. 把J的元素放到HashSet中
2. Traverse S中的元素看是否在HashSet中，在count++

碰到要判断String中char的题要用 for(char c : str.toCharArray())

#####Code


```
 public int numJewelsInStones(String J, String S) {
        int count = 0;
        
        Set setJ = new HashSet();
        
        //access each char using .toCharArray
        for(char j : J.toCharArray()) setJ.add(j);
        //check if s is in setJ
        for(char s : S.toCharArray()){
            if(setJ.contains(s)) count++;
        }
        return count;   
    } 
```

