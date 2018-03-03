![](/assets/Screen Shot 2017-08-29 at 9.55.45 PM.png)

#Analysis
####Idea1:
1.先对list中的interval以start排序，然后依次合并有交集的interval。需要重构一个comparator。
```
public class Solution {
    public List<Interval> merge(List<Interval> intervals) {
        if (intervals == null || intervals.size() <= 1) {
            return intervals;
        }
        
        Collections.sort(intervals, new IntervalComparator());       
  
        List<Interval> result = new ArrayList<Interval>();
        Interval last = intervals.get(0);
        for (int i = 1; i < intervals.size(); i++) {
            Interval curt = intervals.get(i);
            if (curt.start <= last.end ){
                last.end = Math.max(last.end, curt.end);
            }else{
                result.add(last);
                last = curt;
            }
        }
        
        result.add(last);
        return result;
    }
    
    
    private class IntervalComparator implements Comparator<Interval> {
        public int compare(Interval a, Interval b) {
            return a.start - b.start;
        }
    }

}

```

#####Idea2:
1. 若区间为0~1个，直接返回
2. 给区间按 start 元素排序
3. 若重合（ next.start<this.end ）取两个 end 元素得较大值
4. 若不重合，则这个区间不能再合并了，添加到 result 里面

注意：
1. 用到Java8 lamba的表达是来sort
2. add an Interval to result, should new an Interval
3. add the last Interval to result, because it can't pass the if statement in for loop

The idea is to sort the intervals by their starting points. Then, we take the first interval and compare its end with the next intervals starts. As long as they overlap, we update the end to be the max end of the overlapping intervals. Once we find a non overlapping interval, we can add the previous “extended” interval and start over.

Sorting takes O(n log(n)) and merging the intervals takes O(n). So, the resulting algorithm takes O(n log(n)).

I used an a lambda comparator (Java 8) and a for-each loop to try to keep the code clean and simple.



```
public List<Interval> merge(List<Interval> intervals) {
    if (intervals.size() <= 1)
        return intervals;
    
    //* Sort by ascending starting point using an anonymous Comparator
    intervals.sort((i1, i2) -> Integer.compare(i1.start, i2.start));
    
    List<Interval> result = new LinkedList<Interval>(); //*use linkedList
    int start = intervals.get(0).start; //*
    int end = intervals.get(0).end;
    
    for (Interval interval : intervals) {
        if (interval.start <= end) // Overlapping intervals, move the end if needed
            end = Math.max(end, interval.end);
        else {                     // Disjoint intervals, add the previous one and reset bounds
            result.add(new Interval(start, end));
            start = interval.start;
            end = interval.end;
        }
    }
    
    // Add the last interval
    result.add(new Interval(start, end));
    return result;
}
```

#####Sytax:
LinkedList
1. list.get(index) : access elements by index

Math
1. Math.max(,) / Math.min(,)

![](/assets/Screen Shot 2017-08-31 at 3.15.03 PM.png)