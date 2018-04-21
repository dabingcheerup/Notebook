####Idea

The idea is to use one hash set to record sum of every digit square of every number occurred. Once the current sum cannot be added to set, return false;(**detect infinite loop**) once the current sum equals 1, return true;


####Code

```
Set<Integer> inLoop = new HashSet<Integer>();
    int squareSum,remain;
	while (inLoop.add(n)) {
		squareSum = 0;
		while (n > 0) {
		    remain = n%10;
			squareSum += remain*remain;
			n /= 10;
		}
		if (squareSum == 1)
			return true;
		else
			n = squareSum;

	}
	return false;
```

