# Variables

## Types of variables:

### 1. Local Variables

-A variable defined within a block or method or constructor is called local variable. 1.1. These variable are created when the block in entered or the function is called and destroyed after exiting from the block or when the call returns from the function. 1.2. The scope of these variables exists only within the block in which the variable is declared. i.e. we can access these variable only within that block.

### 2. Instance Variables

-Instance variables are non-static variables and are declared in a class outside any method, constructor or block. 2.1 As instance variables are declared in a class, these variables are created when an object of the class is created and destroyed when the object is destroyed. 2.2 Unlike local variables, we may use access specifiers for instance variables. If we do not specify any access specifier then the default access specifier will be used.

### 3. Static Variables

## Scope of Variables

### Member Variables \(Class Level Scope\)

1. must be declared inside class \(outside any function\). They can be directly accessed anywhere in class.

### Local Variables \(Method Level Scope\)

1. Variables declared inside a method have method level scope and can’t be accessed outside the method.
2. Local variables don’t exist after method’s execution is over.

### Loop Variables \(Block Scope\)

1. A variable declared inside pair of brackets “{” and “}” in a method has scope withing the brackets only.

### Some Important Points about Variable scope in Java:

1. In general, a set of curly brackets { } defines a scope.
2. In Java we can usually access a variable as long as it was defined within the same set of brackets as the code we are writing or within any curly brackets inside of the curly brackets where the variable was defined.
3. Any variable defined in a class outside of any method can be used by all member methods.
4. When a method has same local variable as a member, this keyword can be used to reference the current class variable.
5. For a variable to be read after the termination of a loop, It must be declared before the body of the loop.

### [‘this’](https://www.geeksforgeeks.org/this-reference-in-java/)

1. ‘this’ is a reference variable that refers to the current object which is current **class variable**.

