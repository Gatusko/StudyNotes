# QuickSelect
This Algorith works for getting the smallest Element
in a list that is not sorted. This is similar of the **QuickSort
Algorithm** 

For this Algorithm we need to select a Pointer. 
Best if that Pointer is select by a Random Value then 
iterate from  `left pointer to right pointer-1 ` then
move the Pointer to the correct pivot value. The Pivot Value
will start with 0 and move on when match the condition.
# Code 

```java
  public class QuickSelect{
    public static int findKthLargest(int[] nums, int k) {
        // Pivot will be always the last element
        // the Begin will be always the start of the array
        return   quickSelect(nums,0,nums.length-1,nums.length-k);
    }

    private static int quickSelect(int[] nums, int low, int hi, int k) {
        // Store the current Pivot
        int pivotReal=nums[hi];
        // Left Pivot that will be the one to replace
        int currentPivot=low;
        for(int i=low;i<hi;i++)
        {
            // if our current value of our array is less than our pivot the swap with
            // the current pivot and sum by one the pivot
            if(nums[i]<=pivotReal)
            {
                int tempValue=nums[currentPivot];
                nums[currentPivot]=nums[i];
                nums[i]=tempValue;
                currentPivot=currentPivot+1;
            }
        }
        // Make a swap with your right pointer to the final current pivot value
        int tempValue =nums[currentPivot];
        nums[currentPivot]=nums[hi];
        nums[hi]=tempValue;
        // If our current pivot value is bigger  our Element to search
        // then search the left side minus one
        if (currentPivot>k)
        {
            return   quickSelect(nums,low,currentPivot-1,k);
        }
        // Else if our current pivot is less than our K element to search
        // then search the Right side
        else if (currentPivot<k){
            return quickSelect(nums,currentPivot+1,hi,k);
        }
        // Else return the largest K element
        else{
            return nums[currentPivot];
        }
    }
}
```

# Example Step by Step
Get Smallest element of position 1

```
Array : 
{3,2,4,5,6}
Pivot Value = 0;  
Low=0;  
Right=Array.length-1; 
``` 
Select Pointer in this scenario always the Right  
```
{3,2,4,5} --> Pointer 6
3 is Less than 6? -- > Yes, sum Pivot + 1
Pivot Value = 1;
2 is Less than 6? -- > Yes, sum Pivot + 1
Pivot Value = 2;
4 is Less than 6? -- > Yes, sum Pivot + 1
Pivot Value = 3;
5 is Lest than 6? -- > Yes, sum Pivot + 1
Pivot Value = 4;
```

Finish Move Pointer to our current Pivot   
```
{3,2,3,5,6}
{0,1,2,3,4}
Position1 == PivotValue? No 
Position1 < PivotValue ? call Again in a new Partition as 
maxValue-1 partition(low,pivotValue-1,Array);
```
New Partition`(Low=0,Right=3,Array)` 
```
{3,2,4,5}
Pivot Value = 0; // Pivot Value will be Always Low 
Low=0;
Right=3;
Iterating
3 is Less than 5? -- > Yes, sum Pivot + 1
Pivot Value = 1;
2 is Less than 5? -- > Yes, sum Pivot + 1
Pivot Value = 2;
4 is Less than 5? -- > Yes, sum Pivot + 1
Pivot Value = 3;

Finish Move Pointer to our current Pivot
{3,2,4,5}
{0,1,2,3}
Position1 == PivotValue? No
Position1 < PivotValue ? call Again in a new Partition as 
maxValue-1 partition(low,pivotValue-1,Array);
```

New Partition`(low=0,Right=2,Array)`
```
{3,2,4}
Pivot Value = low;// Will be Always Low
Low=0;
Right=2;

3 is Less than 4? -- > Yes, sum Pivot + 1
Pivot Value = 1;
2 is Less than 4? -- > Yes, sum Pivot + 1
Pivot Value = 2;

Finish Move Pointer to our current Pivot
{3,2,4}
{0,1,2}

Position1 == PivotValue? No
Position1 < PivotValue ? call Again in a new Partition as 
maxValue-1 partition(low,pivotValue-1,Array);
```
New Partition`(Low=0,Right1,Array)`

```
{3,2}
Pivot Value = 0;
Low=0;
Right=Array.Length-1;
3 is Less than 2? -- > No. don't add nothing to Pivot
Pivot Value = 0;

Finish Move Pointer to our current Pivot
{2,3}
{0,1}

Position1 == PivotValue? No
Position1 < PivotValue ? No
Position1 > PivotValue ? Yes, the new low will be currentPivot 
plus+1 and the right will be the same 
partition(currentPivot+1,right,Array);
```
New Partition`(Low=1,Right=1,Array)`
```
{3}
PivotValue=1; // Pivot will be Always Low
Low=1;
Right=1;
Can't move more go the last step
Finosh Move Pointer to our Current Pivot
{3}
{1}
Position1 == PivotValue? Yes. Return 3.
```
This average case is O(N). Worst case scenarios is O(N*N) so for avoiding this 
is better to select a random Pointer. 
