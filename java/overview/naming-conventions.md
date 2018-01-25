###Class and Interface
1. Class name - **nouns**
2. Class name and interface name: the first letter of each internal word capitalized
3. Use whole words and must avoid acronyms and abbreviations.(Bicyle)

###Methods : 
1. Methods - **verbs**
2. the first letter lowercase and with the first letter of each internal word capitalized. (speedUP)

###Variables : 
1. Variable names should be short yet meaningful.
2. Should not start with underscore(‘_’) or dollar sign ‘$’ character.
3. should be mnemonic i.e, designed to indicate to the casual observer the intent of its use.
4. One-character variable names should be avoided except for temporary variables.
 Common names for temporary variables are i, j, k, m, and n for integers; c, d, and e for characters.

###Constant variables:
1. all uppercase with words separated by underscores (“_”).
There are various constants used in predefined classes like Float, Long, String etc.

###Packages:
1. The prefix of a unique package name is always written in all-lowercase ASCII letters and should be one of the top-level domain names, like com, edu, gov, mil, net, org.
2. Subsequent components of the package name vary according to an organization’s own internal naming conventions.

##[file name and class name in Java](https://www.geeksforgeeks.org/myth-file-name-class-name-java/)
1. In java file name and class name should be the same.
2. If different, Command javac fileName is run and create a className.class without any error message since **the class is not public**
3. It is possible to have many classes in a java file. For debugging purposes. Each class can be executed separately to test their functionalities(only on one condition: Inheritance concept should not be used).**Javac Trial.java** will create two .class files as **ForGeeks.class and GeeksTest.class** .
Since each class has separate main() stub they can be tested individually.
When **java ForGeeks** is executed the output is For **Geeks class**.
When **java GeeksTest** is executed the output is **Geeks Test class**.