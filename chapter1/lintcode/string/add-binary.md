![](/assets/Screen Shot 2017-08-23 at 8.22.33 PM.png)
#Analysis
####Idea:
1. 方法二：将长的那个数放在前，短的数放在后。用carriers记录进位。然后从后往前将两个数对应的位置上的数相加上carriers，将结果%2加入res之前，同时用结果/2来更新carriers。当短的数到头之后，则只要将长的数的位上的数和carriers相加即可。最后当长的数也到头之后，若carriers为1，则在res前加"1"即可。
    注意：
    1. Reverse 因为用了StringBuilder.append()，数字都反了
    2. 同时要把sb转换为String再返回
2. 方法一：将两个数转换成二进制整数，然后用位运算进行相加，再将所得结果用二进制string表示。



```
public class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i = a.length() - 1, j = b.length() -1, carry = 0;
        while (i >= 0 || j >= 0) { //*
            int sum = carry; //*
            if (j >= 0) sum += b.charAt(j--) - '0'; //*
            if (i >= 0) sum += a.charAt(i--) - '0';
            sb.append(sum % 2);
            carry = sum / 2;
        }
        if (carry != 0) sb.append(carry);
        return sb.reverse().toString(); //*
    }
}
```

