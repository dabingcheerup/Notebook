---
description: Easy
---

# Student Attendance Record I

You are given a string representing an attendance record for a student. The record only contains the following three characters:

1. **'A'** : Absent.
2. **'L'** : Late.
3. **'P'** : Present.

A student could be rewarded if his attendance record doesn't contain **more than one 'A' \(absent\)** or **more than two continuous 'L' \(late\)**.

You need to return whether the student could be rewarded according to his attendance record.

**Example 1:**  


```text
Input: "PPALLP"
Output: True
```

**Example 2:**  


```text
Input: "PPALLL"
Output: False
```

**Analysis**

count the num of each char, if satisfy the following condition:

\#A &lt;= 1, \#L &lt;= 2, then return true

**Pseudocode:**

```java
Class Solution {
    public boolean checkRecord(String s) {       
        int num_A=0, num_L=0, num_P=0;       
        for (char ch: s.toCharArray()){
            if (ch == 'A') num_A++;
            else if(ch == 'L') num_L++;
            else if(ch == 'P') num_P++;
        }
        return (num_A <=1 && num_L <= 2);
    }
}
```

{% hint style="danger" %}
Compile Error

1. Playground Debug Line 6: error: incomparable types:  char and String else if\(ch == "L"\) num\_L++; 
   1. **Single quote for char, double quotes for String** ch == 'L'
{% endhint %}

{% hint style="danger" %}
题目没仔细看

doesn't contain **more than one 'A' \(absent\)** or **more than two continuous 'L' \(late\)**.

怎么算continuous ‘L'？

1. 每次遇到 ’A‘ or 'P', num\_L = 0
2. 当遇到 'L'，num\_L++，且接着判断是否 num\_L &gt; 2, 是return false
3. TESTCASE:     "LLLALL"    false
{% endhint %}

**Java - M1**

```java
class Solution {
    public boolean checkRecord(String s) {       
        int num_A=0, num_L=0;       
        for (char ch: s.toCharArray()){
            if (ch == 'A'){ 
                num_A++;
                num_L = 0;
            }
            else if(ch == 'L') { 
                num_L++;
            }
            else {
                num_L = 0;
            }
            if (num_A > 1 || num_L > 2) return false;
        }
        return true;
    }
}

9 ms
```

**Java - Regex**

```java
public boolean checkRecord(String s) {
    return !s.matches(".*LLL.*|.*A.*A.*");
}
```

**Java - Methods**

```java
public class Solution {
    public boolean checkRecord(String s) {
        if(s.indexOf("A") != s.lastIndexOf("A") || s.contains("LLL"))
            return false;
        return true;
    }
}
```

**Python**

```python
def checkRecord(self, s):
        return len(s.split('A'))<=2 and s.find('LLL')==-1
```

