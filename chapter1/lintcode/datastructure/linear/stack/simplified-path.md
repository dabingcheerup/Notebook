![](/assets/Screen Shot 2018-03-04 at 4.35.53 PM.png)

#####Idea
1. preprocess, path.split("/")
    reducdunt / becomes "", will be ignored
2. if met "..", stack.pop()
3. else push every valid file name into stack, exclude ".", "..", ""
4. generate simplified path using stack
    if nothing generated return "/"    

```
 public String simplifyPath(String path) {
        Deque<String> stack = new LinkedList<String>();
        Set<String> ignore = new HashSet<>(Arrays.asList(".", "..","")); //*
        for(String dir : path.split("/")){
            if(dir.equals("..") && !stack.isEmpty()) stack.pop();
            else if(!ignore.contains(dir)) stack.push(dir);
        }
        //generate simplified path using stack
        String res = "";
        for(String dir : stack){
            res = "/" + dir + res;
        }
        
        return res.isEmpty() ? "/" : res;
    }
```

#####Syntax
```

Stack
1. Deque<String> stack = new LinkedList<String>()
2. stack.isEmpty()

[HashSet](https://www.tutorialspoint.com/java/util/java_util_hashset.htm)
1. Set<String> set = new HashSet<>(Arrays.asList())
2. set.contains()

Arrays
1. [Arrays.asList()](https://www.tutorialspoint.com/java/util/arrays_aslist.htm)

String
1. str.equals()

```

