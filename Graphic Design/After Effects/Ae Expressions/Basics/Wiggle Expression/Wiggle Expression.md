the basic form goes like this: 
```plaintext
wiggle (); 
```
and it usually contains two values: frequency and amplitude like this: 
```plaintext
wiggle (5,30)
```
the ::5:: means that I want to wiggle five times in one second. 
the ::30:: means that the maximum amount (positive or negative) of this value or property will wiggle in one second.
to wiggle a 2D Layer (position for example with x and y), you have to reference an array in your code: 
```plaintext
[value[0],wiggle(8,3)[1]];
```
::value[0]::refers to the x value. 
::value[1]:: refers to the y value. 


