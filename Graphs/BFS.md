# BFS (Breadth First Search)
A way to traverse an intere graph visiting first the neightborhood
nodes. This BFS is good for get the Shortest Path between two nodes

For traverse with BFS we will need two things 
1. Queue for adding the visited Nodes and then iterate over them.
2. Array,Set for knowing if the node is already visited.

For example:  
```
     a
    /  \
  b      c
 /  \   /  \   
d   e f    g
```
So for traverse with BFS this tree we will need first a 
Queue and the Set of nodes visited
```Add to our Queue --> a 
Add to our set visisted --> a 
while the queue is not empty 
node -> poll from the queue
iterate the edge nodes of the Node
if edge node is not in the Set Of Visisted the
visisted the Node and add to our queue

Step by Step 
Add to our Queue --> a
Add to our Set Visited-->a
start while
queue is not empty
poll a 

Iterate the edges of a

b is not in the set of Visisted
b Add to our Queue --> b
b Add to our Set visisted--> b

c is not in the set of Visisted
c Add to our queue --> c
c Add to our Set visited --> c

Queue -->  b,c 
Set of visisted ==> a,b,c
queue is not empty
poll b 
Iterate the edges of b

d is not in the set of Visisted 
d Add to our queue --> d
d Add to our Set Visited --> d

e is not in the set of visisted
e Add to our queue --> e
e Add to our set Visisted -- > e

poll c

Iterate over the edges of c

f is not in the set of Visisted
f add to our queue --> f
f add to our Set visisted --> f

g is not in the Set of visisted
g add to our queue --> g
g add to our Set visisted --> g

Queue --> d,e,f,g
Set visisted --> a,b,c,d,e,f,g

Queue is not empty
poll d
d --> doesn't have edge nodes.
Queue --> e,f,g
poll e 
e -- >doesn't have edge nodes.
Queue --> f,g 
poll f 
f-->doesn't have edge nodes.
Queue --> g
poll g
g-->doesn't have edge nodes.
Queue is empty. Graph was traverse with BFS
``` 

With BFS we can get the Shortest Path on a unweighted graph
# Example of BFS
[Leet Code Problem Shortest Path](https://leetcode.com/problems/word-ladder/).  

```java
/*
        Given two words, beginWord and endWord, and a 
        dictionary wordList, return the number of words 
        in the shortest transformation sequence from beginWord 
        to endWord, or 0 if no such sequence exists.
        word can only modify by one Letter
 */
class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
       // You can initialize a set with an Array List
        Set<String> mySetOfWords=new HashSet<>(wordList);
        // If my Set doesn't contain my word so return 0
        if(!mySetOfWords.contains(endWord))
        {
            return 0;
        }
        Queue<String> myQueue=new LinkedList<>();
        // We start our graph with the first word to try to find the shorthest path
        myQueue.add(beginWord);
        int numberOfSteps=1;
        Set<String> vistiedStrings=new HashSet<>();
        vistiedStrings.add(beginWord);
        while (!myQueue.isEmpty())
        {
            int size= myQueue.size();
            // we iterate over the nodes and see the possible neigbohours
            for(int i=0;i<size;i++)
            {

                String toPoll=myQueue.poll();
                // If the polled word equals to our end world then
                // we reach to our final node
                if(toPoll.equals(endWord))
                {
                    return numberOfSteps;
                }
                // Code to modify only character of the String letter.
                // this is only for lowercase strings
                // for example we have the string abc
                // we will modifi a - > to b,c,d,e,f with bc
                // for b --> a --> a,c,d,e,f,g -->c
                // for c --> ab --> a,b,d,e,f,g
                for(int j = 0; j < toPoll.length(); j++){
                    for(int k = 'a'; k <= 'z'; k++){
                        char arr[] = toPoll.toCharArray();
                        arr[j] = (char) k;

                        String str = new String(arr);
                        if(mySetOfWords.contains(str) && !vistiedStrings.contains(str)){
                            myQueue.add(str);
                            vistiedStrings.add(str);
                        }
                    }
                }
            }
            // we increase the number of steps plus one
            numberOfSteps=numberOfSteps+1;
        }
        //if is not reached
        //then return by 0
        return 0;
    }
}
```