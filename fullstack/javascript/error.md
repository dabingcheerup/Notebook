# error

1. [Uncaught TypeError: Cannot set property 'onclick' of null ](https://stackoverflow.com/questions/17080502/uncaught-typeerror-cannot-set-property-onclick-of-null)

execute the script after the DOM is ready like:

```text
window.onload = function(){
    document.getElementById("subm").onclick=function(){
        alert("Hello WOrld");
    }
}
```

