# Tabulation

In this approach we go from the base case to the final case. Also know as 
**Bottom Up**. This is iterative and need to understand a lot the conditions.

For example  
Coin Change 
Giving an Array of Coins `{2,5}` give the less coins needed for giving a 
change.  
For example 13
The minimum of Coins is 5 : {2,2,2,2,5} 
For this solution the bottom-up Tabulation approach is to understand and
get the base cases. 
First get our Array of 13+1 

|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  0 | 0  |0   |0   |0   | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |

So we start goin step by step filling our scenarios base case is 0 is 0.
Now lets go step by step.  
Change 1.
```
1-DP{Change-coins[i]} ==> 1+DP{1-2} ==> Negative so Cero
1+DP{1-5} == > Negative so Cero. 
```
So we can give any change to 1 with the coins {2,5}

|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 0  |0   |0   |0   | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |


Change 2.   
```
1+DP{Change+coinbs[i]} ==> 1+DP{2-2}  
1+DP{0} == > DP{0}==1. So we add 1 to our current Value. Minimum is always 1.
Move on.
```

|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |0   |0   |0   | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |


Change 3.  
```
1+DP{Change+coins[i]}==> 1+DP{3-2}=> 1+DP{1} ==> Negative value in 1 so we check next coin 
1+DP{3-5}. Negative for checking the less change move and say we can modify 3.
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |0   |0   | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |

Change 4.
```
1+DP{4-2} ==>1+DP{2}==>1+1 ==> 2 Current Less Value check next coin. 
1+DP{4-5}==> Negative is our current LEss check Value
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |0   | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |

Change 5.  
```
1+DP{5-2} ==> 1+DP{3} ==>is Negative Store so move on next coin
1+DP{5-5}=> 1+DP{0} => 1 store it as 1 is the minimum value.
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 0  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |

Change 6. 
```
1+DP{6-2} ==> 1+DP{4} ==>1+2==> Current Minimum value is 3
1+DP{6-5}==> 1+DP{1} ==> Negative store in the current value lest store
3
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 0  | 0  | 0  | 0  | 0  | 0  | 0  |

Change 7. 
```
1+DP{7-2}==>1+DP{5}==>2 Let's store 2 as our minimum value
1+DP{7-5}==>1+DP{2}==>2 is equal to our current minimum value let's store it in our DP Array
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 0  | 0  | 0  | 0  | 0  | 0  |

Change 8. 
```
1+DP{8-2}==>1+DP{6}==>4 Current minimun value is 4.
1+DP{8-5}==>1+DP{3}==>NEgative let's store 4.
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 4  | 0  | 0  | 0  | 0  | 0  |

Change 9.
```
1+DP{9-2} ==> 1+DP{7} ==> 3 Current Minum Value is 3.
1+DP{9-5} ==> 1+DP{4} ==> 3 It is equal to our current Minum Value. Store
3 in our DP Array
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 4  | 3  | 0  | 0  | 0  | 0  |

Change 10. 
```
1+DP{10-2} ==> 1+DP{8}==> 5 Current Minum Value is 5.
1+DP{10-5}==>1+DP{5}==> 2 This is less than our current minum value store
2 in our DP Array
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 4  | 3  | 2  | 0  | 0  | 0  |

Change 11.
```
1+DP{11-2} ==> 1+DP{9}==>4 Current Minimum Value is 4
1+DP{11-5}==>1+DP{6}==>4 it is equal to our current minium value store
it in our DP Array
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 4  | 3  | 2  | 4  | 0  | 0  |

Change 12. 
```
1+DP{12-2}==> 1+DP{10}==>3 Current Minimun value is 3.
1+DP{12-5}==> 1+DP{7}==>3 It's equal to our current minimun value. Store 3
in our DP Array.
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 4  | 3  | 2  | 4  | 3  | 0  |


Change 13.
```
1+DP{13-2} 1+DP{11} ==> 5 Current minimun value is 5.
1+DP{13-5}==>1+DP{8}==>5 It's equal than our current minimun value. Store 
5 in our DP Array
```
|0   |1   | 2  | 3  |4   |5   |6   |7   |8   | 9  |10   | 11  | 12   | 13   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0  |  -1 | 1  |-1   |2  |1 | 3  | 2  | 4  | 3  | 2  | 4  | 3  | 5  |



Get DP{13} ==> 5 Is our current Minimun Value.

# Notes 
Tabulation is more faster, but harder to come when the conditions 
are very to use it. This is just one scenario of tabulation with this DP
problem. Always to the Start to the End to get the results. 