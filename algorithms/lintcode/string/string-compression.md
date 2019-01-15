---
description: Easy
---

# String Compression

Given an array of characters, compress it [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm).

The length after compression must always be smaller than or equal to the original array.

Every element of the array should be a **character** \(not int\) of length 1.

After you are done **modifying the input array** [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm), return the new length of the array. 

**Follow up:**  
Could you solve it using only O\(1\) extra space? 

**Example 1:**

```text
Input:
["a","a","b","b","c","c","c"]

Output:
Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]

Explanation:
"aa" is replaced by "a2". "bb" is replaced by "b2". "ccc" is replaced by "c3".
```

**Example 2:**

```text
Input:
["a"]

Output:
Return 1, and the first 1 characters of the input array should be: ["a"]

Explanation:
Nothing is replaced.
```

**Example 3:**

```text
Input:
["a","b","b","b","b","b","b","b","b","b","b","b","b"]

Output:
Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].

Explanation:
Since the character "a" does not repeat, it is not compressed. "bbbbbbbbbbbb" is replaced by "b12".
Notice each digit has it's own entry in the array.
```

**Note:**

1. All characters have an ASCII value in `[35, 126]`.
2. `1 <= len(chars) <= 1000`.

**Analysis:**

count consecutive char, than replace substring\(start, i\) with 'char\#' like 'a2'

**Pseudocode:**

```java
class Solution {
    public int compress(char[] chars) {
        int count = 1, start = 0, len = chars.length;
        
        if (len < 2) {
            return len;
        }
        StringBuilder compression = new StringBuilder();
        String s = chars.toString();
               
        for (int i = start+1; i < len; i++) {
            if (chars[start] == chars[i]) count++;
            else {
                compression.append(chars[i]+count.toString());
                s.replaceFirst()
                start = i;
            }
        }
    }
}
```

{% hint style="info" %}
Code

用StringBuilder在原有的String上替换涉及到index，比较麻烦

因此，curChar记录当前要数的char, 直到数完，把curChar替换到chars\[indexAns++\]，意思替换完后，indexAns +1,  指向下一个位置，所以再把前一个char的个数替换到indexAns上，然后indexAns+1。即：

chars\[indexAns++\] = curChar;

chars\[indexAns++\] = c
{% endhint %}

**Java**

```java
    public int compress(char[] chars) {
        int indexAns = 0, index = 0;
        while(index < chars.length){
            char currentChar = chars[index];
            int count = 0;
            while(index < chars.length && chars[index] == currentChar){
                index++;
                count++;
            }
            chars[indexAns++] = currentChar;
            if(count != 1)
                for(char c : Integer.toString(count).toCharArray()) 
                    chars[indexAns++] = c;
        }
        return indexAns;
    }
```

{% hint style="info" %}
Grammar

把num转成String： **Integer.toString\(num\)**
{% endhint %}

