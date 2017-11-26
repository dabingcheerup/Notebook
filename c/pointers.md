

```
char *str;
str = "http://c.biancheng.net";

```

字符串中的所有字符在内存中是连续排列的，str 指向的是字符串的第 0 个字符；我们通常将第 0  个字符的地址称为字符串的首地址。字符串中每个字符的类型都是char，所以 str 的类型也必须是char *。

C语言有两种表示字符串的方法，一种是字符数组，另一种是字符串常量，它们在内存中的存储位置不同，使得字符数组可以读取和修改，而字符串常量只能读取不能修改。

[void pointers advantage](http://www.geeksforgeeks.org/void-pointer-c/) 
1. void pointers in C are used to implement generic functions in C. 
2. malloc() and calloc() return void * type and this allows these functions to be used to allocate memory of any data type (just because of void *)