# MinHeap 
This data structure in Java can be used with the **Priority Queue** 
Object. By default this is a Tree that the root node will be always
the less Integer. So in Theory it will be the less value for every poll.

![](MinHeap.png)

# Example
In Java less go step by step. 

As we are using Integer by Default it will try to compare and 
for evey poll get always the lest value. 

      PriorityQueue<Integer> myPriorityQueue=new PriorityQueue<>();
      myPriorityQueue.add(5);
      myPriorityQueue.add(7);
      myPriorityQueue.add(8);
      myPriorityQueue.add(9);
      myPriorityQueue.add(2);
      myPriorityQueue.add(3);

In here we saw that we add : 5,7,8,9,2,3. 

And the polling Will be the next

      System.out.println(myPriorityQueue.poll()); // OutPut will be 2
      System.out.println(myPriorityQueue.poll()); // OutPut will be 3
      System.out.println(myPriorityQueue.poll()); // OutPut will be 5
      System.out.println(myPriorityQueue.poll()); // OutPut will be 7
      System.out.println(myPriorityQueue.poll()); // OutPut will be 8
      System.out.println(myPriorityQueue.poll()); // OutPut will be 9

Final OutPut  
```2  
3  
5  
7  
8  
9 
1
```

# Example on Problem 
Merge N Lnked Lists that are sorted as ascending form. 
[Leet Code Problem  ](https://leetcode.com/problems/merge-k-sorted-lists/submissions/)
 
```java
public class ExampleOfMinHeap{
    /*
Give the Lists {1,3,5} , {2,4,6}
We add to our PriorityQueue= {1,3,5,2,4,6} == > This will be a Min Heap.
For Every poll of Data we will be get the less Value.
poll ==> 1
poll ==> 2
poll ==> 3
poll ==> 4
poll ==> 5
poll ==> 6        
*/
    public static ListNode mergeKLists2(ListNode[] lists) {
        if(lists==null)
        {
            return null;
        }
        if(lists.length==0)
        {
            return null;
        }
// All the values in our lists are Integer so we use MinHeap to make this work
        PriorityQueue<Integer> myPriorityQueue=new PriorityQueue<>();
        for(int i=0;i<lists.length;i++)
        {
            ListNode myHead=lists[i];
            while (myHead!=null)
            {
                myPriorityQueue.add(myHead.val);
                myHead=myHead.next;
            }
        }
        if(myPriorityQueue.isEmpty())
        {
            return null;
        }
        ListNode myNode=new ListNode();
        ListNode pointOfMyHead=myNode;
// We go step by step polling data
        while (!myPriorityQueue.isEmpty())
        {
// We poll the Data to add to our current node
            myNode.val=myPriorityQueue.poll();
            if(myPriorityQueue.isEmpty())
            {
                break;
            }
            myNode.next=new ListNode();
            myNode=myNode.next;
        }
        return pointOfMyHead;
    }
}
```