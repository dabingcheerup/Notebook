In C, functions can return any type except arrays and functions. We can get around this limitation by returning pointer to array or pointer to function

Empty parameter list in C mean that the parameter list is not specified and function can be called with any parameters. In C, it is not a good idea to declare a function like fun\(\). To declare a function that can only be called without any parameter, we should use “void fun\(void\)”.
As a side note, in C++, empty list means function can only be called without any parameter. In C++, both void fun() and void fun(void) are same.
