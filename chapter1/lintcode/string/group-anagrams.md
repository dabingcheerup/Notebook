#####Idea:
1. HashMap key 存放 anagrams, value 存放对应group(List\<\String\>\)
2. traverse strs, convert each string to char array, then sort it, and compare to anagram.
3. 注意
    1. 用变量存放sorted char array
    2. map中新加入的anagrams的value要new一个ArrayList存放s
    3. 最后把所有s按anagram分别放入对应的group后，要把map转变为ArrayList返回
    
#####code


```
public class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        if (strs == null || strs.length == 0) return new ArrayList<List<String>>(); //*
        Map<String, List<String>> map = new HashMap<String, List<String>>(); //*
        //*convert each string to char[] array
        for (String s : strs) {
            char[] ca = s.toCharArray();
            Arrays.sort(ca);
            String keyStr = String.valueOf(ca); //*
            if (!map.containsKey(keyStr)) map.put(keyStr, new ArrayList<String>()); //*
            map.get(keyStr).add(s);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```
#####Error


```
error: no suitable method found for put (String,ArrayList <String>)
原因：
Map<String, List<String>> map = new HashMap<String, Integer>();
map.put(anagram, new ArrayList<>());
改进： value需是 List<String>() 才能put ArrayList
Map<String, List<String>> map = new HashMap<String, List<String>>();

```


#####Syntax
String
1. strName.toCharArray()
2. String.valueOf(); //convert to String type

Char Array
1. Arrays.sort(charArr)

HashMap
1. map.put(key, value)
2. map.get(key)
3. map.containsKey()
4. map.values() //The values() method is used to return a Collection view of the values contained in this map.

ArrayList
1. new ArrayList<List<\/String>>(map.values())

