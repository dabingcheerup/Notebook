# Roman to integer

## Idea:

1. HashMap存放Roman-Integer的映射
2. 按Roman-Integer的converting ruls来读取s

    从index 0开始读

    小数在左就减去，否则加上

   1. 若当前s.charAt\(i\)的值小于s.charAt\(i+1\),res -=map.get\(s.chartAt\(i\)\)
   2. 反之，加上

3. 剩下最后一个数，直接加上。而后返回结果

## Error：

1. if\(i == 0\|\| map.get\(s.charAt\(i\)\) &lt; map.get\(s.charAt\(i-1\)
   1. log: input: "MCMXCVI", expected: 1996 output: 16
   2. 原因：加减顺序不对，不要判断小数是否在右，而是小数是否在左即和i+1比较
   3. 关键：从0开始读取，每次判断该数是要被减还是被加，**取决于它与i+1的比较**

## Code

```text
public int romanToInt(String s) {
        // write your code here
        HashMap<Character, Integer> map = new HashMap<Character, Integer>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);

        int res = 0;

        // traverse s
        for(int i = 0; i < s.length()-1; i++){
            //小数在左就减去
            if(map.get(s.charAt(i)) < map.get(s.charAt(i+1))){ //**
                res -= map.get(s.charAt(i));
            }else{
                res += map.get(s.charAt(i));
            }
        }
        return res + map.get(s.charAt(s.length()-1));
    }
```

## Syntax：

HashMap 1. Constructor： HashMap map = HashMap\(\) 2. HashMap.put\(Key, Value\): inset a pair 3. HashMap.get\(Key\): get the value of the key

