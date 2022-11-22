# Check if a String A is a subString of String B.(AnyOrder)

For knowing if String A is a subString of String B and 
the order of String A doesn't matter. We need to map the
characters of String A and Iterate over String B with a Counter
for every character found on the map of String A substract minus
1 and increase counter. If the Counter at the end is equal to
the length of the String A then String B contains the String A 
in any order.

# Example 
```
String A : "bcc"
String B : "abbcdc"

Map String A Characters 
b -- > 1
c -- > 2 

Counter = 0;
Iterate over String B 
a --> is On the Map ? No. 
b --> is On the Map ? Yes. Is greater than Cero? Yes. Decrease
on the Map of String A Characters and Increase Counter by one.

Map String A Characters
b -- > 0
c -- > 2 

Counter = 1;

b--> is On the Map> Yes. Is on the Map Greater than cero? No. Move on
c--> is On the Map? Yes. Is on the Map Greater than Cero? Yes.
Decrease on the Map Of String A Characters and Increase counter by one.

Map String A Characters
b -- > 0
c -- > 1

Counter = 2;

d--> is on the Map? No
c--> Is on the Map? Yes. Is on the Map Greater than cero? Yes.
Decrease on the Map Of String A Characters and Increase counter by one.

Map String A Characters
b -- > 0
c -- > 0

Counter = 3;

is Counter equals to the lenth of String A ? 
Yes. Then String A is a Substring of String B in any order of 
characters.
```
This can be very help to know at time of solving String Problems 
