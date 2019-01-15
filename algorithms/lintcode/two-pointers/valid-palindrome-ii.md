---
description: Easy
---

# Valid Palindrome II

Given a non-empty string `s`, you may delete **at most** one character. Judge whether you can make it a palindrome.

**Example 1:**  


```text
Input: "aba"
Output: True
```

**Example 2:**  


```text
Input: "abca"
Output: True
Explanation: You could delete the character 'c'.
```

**Note:**  


1. The string will only contain lowercase characters a-z. The maximum length of the string is 50000.

**'Analysis:'**

1. only contain lowercase, so two pointer, one points to the start, the other points to the end.
2. if str\[start\] != str\[end\] return false
3. else start++, end--
4. if str\[start\] == str\[end\] and start == end, that means we can delete this char make the string as palindrome

**'Pseudocode:'**

```java
Class Solution {
    public boolean validPalindrome(String s) {
        int left = 0, right = s.length();
        while (left <= right) {
            if (s[])
        }    
    }
}
```

{% hint style="danger" %}
题目理解错误

是指可以删除任何一个字符使得字符串palindrome。

所以当头尾指针的字符不相等，要看是删掉当前头指针所指的字符 - isPalindromic\(s, left, right+1\)，还是删掉尾指针所指的字符 - isPalindromic\(s, left-1, right\)
{% endhint %}

**Java**

```java
Class Solution {
    pubic boolean validPalindrome(String s){
        int left = -1, right = s.length();
        while (++left < --right){
            if (s.charAt(left) != s.charAt(right)) return isPalindromic(s, left-1, right) || isPalindromic(s, left, right+1);
        }
        return true;
    }
    
    public boolean isPalindromic(String s, int left, int right){
        while (++left < --right) {
            if (s.charAt(left) != s.charAt(right)) return false;
        }
        return true;
    }
}
```

**Python**

Whenever there is a mismatch, we can either exclude the character at the left or the right pointer. We then take the two remaining substrings and compare against its reversed and see if either one is a palindrome.

```python
Class Solution:
    def validPalindrome(s):
        left = 0
        right = s.len()-1
        while left < right:
            if (s[left] != s[right]):
                one, two = s[left:right], s[left+1, right+1]
                return one = one[::-1] or two == two[::-1]
            left += 1
            right -= 1
        return Ture
                
```

{% hint style="info" %}
Gramma

1. Suppose we have got `[a: b: c].` **Rules** for indices will be as follows:
   1. First `c` is checked. Default is `+1`, sign of `c` indicates forward or backward direction of the step. Absolute value of `c` indicates the step size.
   2. Then`a` is checked. When `c` is positive or `None`, default for `a` is `0`. When`c` is negative, default for `a` is `-1`.
   3. Finally `b` is checked. When `c` is positive or `None`, default for `b` is `len`. When `c` is negative default for `b` is `-(len+1)`.
{% endhint %}

