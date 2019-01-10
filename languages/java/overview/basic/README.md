# Basic

**Statically typed language:** C, C++, Java: Once a variable is declared to be of a certain data type, it cannot hold values of other data types. **Dynamically typed languages**

Java two categories of data: 1. Primitive data \(e.g., number, character\) 2. Object data \(programmer created types\)

![](http://cdncontribute.geeksforgeeks.org/wp-content/uploads/primitive-data-types-in-java.png)

## [enum](https://www.geeksforgeeks.org/enum-in-java/)

### main objective:

to define our own data types\(Enumerated Data Types\)

### Declaration of enum in java :

Enum declaration can be done outside a Class or inside a Class but not inside a Method.

```text
// A simple enum example where enum is declared
// outside any class (Note enum keyword instead of
// class keyword)
enum Color
{
    RED, GREEN, BLUE;
}

public class Test
{
    // Driver method
    public static void main(String[] args)
    {
        Color c1 = Color.RED;
        System.out.println(c1);
    }
}

Output : RED

// enum declaration inside a class.
public class Test
{
    enum Color
    {
        RED, GREEN, BLUE;
    }

    // Driver method
    public static void main(String[] args)
    {
        Color c1 = Color.RED;
        System.out.println(c1);
    }
}
```

1. First line inside enum should be list of constants and then other things like methods, variables and constructor.
2. According to Java naming conventions, it is recommended that we name constant with all capital letters

### Important points of enum :

1. Every enum internally implemented by using Class.
2. Every enum constant represents an object of type enum.
3. enum type can be passed as an argument to switch statement.
4. Every enum constant is always implicitly public static final. Since it is static, we can access it by using enum Name. Since it is final, we can’t create child enums.
5. We can declare main\(\) method inside enum. Hence we can invoke enum directly from the Command Prompt.

### Enum and Inheritance :

1. All enums implicitly extend java.lang .Enum class. As a class can only extend one parent in Java, so an enum cannot extend anything else.
2. toString\(\) method is overridden in java.lang.Enum class, which returns enum constant name.
3. enum can implement many interfaces.

### values\(\), ordinal\(\) and valueOf\(\) methods :

1. These methods are present inside java.lang.Enum.
2. values\(\) method can be used to return all values present inside enum.
3. Order is important in enums.By using ordinal\(\) method, each enum constant index can be found, just like array index.
4. valueOf\(\) method returns the enum constant of the specified string value, if exists.

### enum and constructor :

1. enum can contain constructor and it is executed separately for each enum constant at the time of enum class loading.
2. We can’t create enum objects explicitly and hence we can’t invoke enum constructor directly.

   **enum and methods :**

3. enum can contain concrete methods only i.e. no any abstract method.

### [Enum with Customized Value in Java](https://www.geeksforgeeks.org/enum-customized-value-java/)

