# MaxHeap
At difference with the MinHeap is that we have the largest value as
the root value and every polling will have the next largest value.
![](MaxHeap.png)

So for doing a MaxHeap in Java we need to said in our comparator that 
will be a reverse or do a custom one. 

`PriorityQueue<Integer> myPriorityQueue=new PriorityQueue<>(Comparator.reverseOrder());
`
With this Comparator REverse Order is the most easy and fastest way 
of approach. Instead of getting the minimum value we are going to get the largest 
because our Comparator is on Reverse Order. 

# Example 
On Java let's go step by step. 
```
      PriorityQueue<Integer> myPriorityQueue=new PriorityQueue<>(Comparator.reverseOrder());
      myPriorityQueue.add(5);
      myPriorityQueue.add(7);
      myPriorityQueue.add(8);
      myPriorityQueue.add(9);
      myPriorityQueue.add(2);
      myPriorityQueue.add(3);
````
In here we saw that we add : 5,7,8,9,2,3.   
And the polling will be like this : 

```
System.out.println(myPriorityQueue.poll()); // OutPut will be 9
System.out.println(myPriorityQueue.poll()); // OutPut will be 8
System.out.println(myPriorityQueue.poll()); // OutPut will be 7
System.out.println(myPriorityQueue.poll()); // OutPut will be 5
System.out.println(myPriorityQueue.poll()); // OutPut will be 2
System.out.println(myPriorityQueue.poll()); // OutPut will be 3
```

And the final output will be like this : 

```
9
8
7
5
3
2
```

# Example on a Problem 
We saw for selecting the Kth Largest Element in an Array we can use 
QuickSelect. But we can use PriorityQueue as MaxHeap.

```java
 public  class MaxHeap{
    public int findKthLargestWithPriorityQueue(int[] nums, int k) {
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Comparator.reverseOrder());
        // Fill our MaxHeap
        for(Integer myInt : nums)
        {
            maxHeap.add(myInt);
        }
        int finalInt=0;
        // poll Our data
        for(int i=0;i<k;i++)
        {
            // We assure that will be always the next Element
            finalInt=maxHeap.poll();
        }
        return  finalInt;
    }
    }
    
```
