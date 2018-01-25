####Types of variables:
#####1. Local Variables
-A variable defined within a block or method or constructor is called local variable.
1.1. 
These variable are created when the block in entered or the function is called and destroyed after exiting from the block or when the call returns from the function.
1.2. 
The scope of these variables exists only within the block in which the variable is declared. i.e. we can access these variable only within that block.

#####2. Instance Variables
-Instance variables are non-static variables and are declared in a class outside any method, constructor or block.
2.1 As instance variables are declared in a class, these variables are created when an object of the class is created and destroyed when the object is destroyed.
2.2 Unlike local variables, we may use access specifiers for instance variables. If we do not specify any access specifier then the default access specifier will be used.
#####3. Static Variables