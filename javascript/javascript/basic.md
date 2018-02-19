Primitive types:
1. Number
2. String
3. boolean
4. null
5. undefine

Collection of data
1. Array

    1. ele can be different types, seperated by ,
    2. arr[index] index is out of bound get error: undefine 
    3. **arr.push("")** add an ele to the end of the arr **arr.pop()** remove and return an ele from the end of the arr
    4. **arr.unshift(""**) add ele to the beginning of **arr.shift()**

2. object
    1. obj.property / obj['property']
    
Dom
acheive html elements by using document.getElementById()

modify them by obj.innerHTML()

localStorage.property: The localStorage variable is an object that maintains the same value for different pages. It cannot, however, be used to access any data on the local computer.

JSON(JavaScript Object Notation) 

    1. JSON.stringify(myObj): JS object can be converted to JSON string representation
    2. JSON.parse(jsonString): JSON string representations can be converted to JS object
    
Using event-driven programming in JavaScript to modify the html base on user activity
Dom event
1. define call back functions for a html element
2. call back functions are invoked by user's events. 
    
    1. create a variable that store the html element acheived by document.getElementById()
    2. variable.addEventListener("eventName", call back function name)
    eventName is a special string like "click", "mouseout", "mouseover", "keyup"(e == 13 means press 'enter' key)
    