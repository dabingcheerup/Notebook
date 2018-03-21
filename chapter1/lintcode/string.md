#####String Class


```
1.String str = "Hello world!"; //create strings

2. str.length() 

3. string1.concat(string2); // This returns a new string that is string1 with string2 added to it at the end. 
    or string1 + string2
4. char str.charAt(int index);  //Returns the character at the specified index.

5. boolean equals(Object anObject);  //Compares this string to the specified object.  The result is true if and only if the argument is not null and is a String object that represents the same sequence of characters as this object.

6. String[] split(String regex);  //Splits this string around matches of the given regular expression.

7. String substring(int beginIndex, int endIndex);  //Returns a new string that is a substring of this string.

8. char[] toCharArray();  //Converts this string to a new character array.

9. String toLowerCase() String toUpperCase()  //Converts all of the characters in this String to upper/lower case using the rules of the default locale.

10. String toString();  //This object (which is already a string!) is itself returned.

11. String trim();  //Returns a copy of the string, with leading and trailing whitespace omitted.








```






[StringBuilder类](https://www.tutorialspoint.com/java/lang/java_lang_stringbuilder.htm)  
1. 不同于String类，不用每次开辟新空间，StringBuild sb = StringBuild\(\)， 给一个空间可以往里不断加  
2. sb.append\(\) 可以叠加 sb.append\(\).append\(\)  
3. sb.substring\(start, end\)

[StringBuffer VS StringBuilder](http://www.runoob.com/java/java-stringbuffer.html)

