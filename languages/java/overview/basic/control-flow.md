# Control flow

## if

## if else

## if else if else

## switch-case

```text
switch (expression)
{
  case value1:
    statement1;
    break;
  case value2:
    statement2;
    break;
  .
  .
  case valueN:
    statementN;
    break;
  default:
    statementDefault;
}
```

1. Expression can be of type byte, short, int char or an enumeration. Beginning with JDK7, expression can also be of type String.

   （[String in switch case](https://www.geeksforgeeks.org/string-in-switch-case-in-java/): 1. string can't be null 2. case sensitive）

2. Dulplicate case values are not allowed.
3. The default statement is optional.
4. The break statement is used inside the switch to terminate a statement sequence.
5. The break statement is optional. If omitted, execution will continue on into the next case.

## jump statement

### 1. break

Used for： 1. switch中 2. loop中，跳出当前整个loop

### 2. continue

1. loop中，跳过剩下的语句，进入新一轮loop

### 3. return

1. return from a method

