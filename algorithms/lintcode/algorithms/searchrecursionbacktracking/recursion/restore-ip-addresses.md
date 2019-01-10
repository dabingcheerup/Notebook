# restore IP addresses

## Idea:

1.这道题其实是将字符串分割成4段，使得结果为合法的IP地址。要求返回所有合法IP地址，想到用递归。 合法的IP地址为：1）由4段组成 2）每一段长度为1到3 3）每一段如果不是0，不能以0开头，如01，00 4）每一段大小不能大于255 用一个result记录合法答案，用一个list纪录当前答案，start代表能够取值的起始位置。 当前段可以取start~start，start~start＋1，start~start＋2这几个字符串，然后递归求下一段。每次取值要检验取的字符串的合法性。 当取满4段时，看此时是否还有字符串剩下，没有则将4段拼成合法的IP地址

```text
public class Solution {
    /*
     * @param s: the IP string
     * @return: All possible valid IP addresses
     */
    public List<String> restoreIpAddresses(String s) {
        // write your code here
        ArrayList<String> result = new ArrayList<String>();
        ArrayList<String> list = new ArrayList<String>();

        if(s.length() <4 || s.length() > 12)
            return result;

        helper(result, list, s , 0);
        return result;
    }

    public void helper(ArrayList<String> result, ArrayList<String> list, String s, int start){
        if(list.size() == 4){
            ////分成4段后若还有字符串剩余则不合法
            if(start != s.length())
                return;
            //每一段后面加"."，再将最后一个"."删去
            StringBuffer sb = new StringBuffer();
            for(String tmp: list){
                sb.append(tmp);
                sb.append(".");
            }
            sb.deleteCharAt(sb.length()-1);
            result.add(sb.toString());
            return;
        }
        //如果该段为3位，则要检验是否超过255
        for(int i=start; i<s.length() && i < start+3; i++){
            String tmp = s.substring(start, i+1);
            if(isvalid(tmp)){
                list.add(tmp);
                helper(result, list, s, i+1);
                list.remove(list.size()-1);
            }
        }
    }
    //合法IP的每一段都小于等于255
    //每一段长度不能超过3，同时如果超过了1位，则不能以0开头，如01
    private boolean isvalid(String s){
        if(s.charAt(0) == '0')
            return s.equals("0"); // to eliminate cases like "00", "10"     
        int digit = Integer.valueOf(s);
        return digit >= 0 && digit <= 255;
    }
}
```

