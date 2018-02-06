![](/assets/Screen Shot 2018-02-06 at 11.20.24 AM.png)

#####Idea
1. 一对对消，消到最后若剩下单个的元素，挑一个放中间；若没有剩下直接返回count

#####数据结构
hashset: contains only unique keys. 
**s.charAt(i)** index 访问 String中的char

#####Sol:
1. init count = 0, hashset hs = new hashset()
2. for loop traverse s:
    1. 在hs中就**remove掉**，像对对碰，count++
    2. 不在hs中就存
3. 每次对碰一次，就相当于result长度加2
    1. 若hs中为空，那么s中所有元素都对碰完，result.length() = count * 2
    2. 若hs中不为空，那么有剩下单的元素，挑一个放中间，result.length() = count * 2 + 1
    
#####Code


```
 public int longestPalindrome(String s) {
        // write your code here
        int count = 0;
        HashSet<Character> hs = new HashSet<Character>();
        
        //traverse s
        for(int i = 0; i < s.length(); i++){
            if(hs.contains(s.charAt(i))){
                hs.remove(s.charAt(i));
                count++;
            }else{
                hs.add(s.charAt(i));
            }
        }
        return hs.isEmpty() ? count * 2 : count * 2 + 1;
    }
```

