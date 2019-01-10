# Widening Primitive Conversion

## " "

1. text in double quotes is treated as **a string**

## ''

1. if '+' operator is present, the character in single quote is converted to int

```text
public class Test
{
    public static void main(String[] args)
    {
        System.out.print("Y" + "O");
        System.out.print('L' + 'O');
    }
}

Actual Output:
“YO155”. 155 = 76 + 79
```

