**if you have a property let's say scale or opacity and it's keyframed on the time line and you don't want to mess up the keyframes, you just want the value to be reduced by 50% you can do that by adding an expression: 
> value -50￼
which will decrease the value by 50 point; you can also apply all kind of operation on the value like adding, subtracting, ect.
if you have two values like x and y you can separate them in the expression like this: 
```plaintext
[x, y] = value; // Destructure the current position into x and y components
x = x - 450; // Apply your desired change to x
y = y - 400; // Or modify y as you wish, for example, y = y - 100;
[x, y] // Return the modified [x, y] array as the new position

```
Now without the Comments
```plaintext
[x, y] = value;
x = x - 450;
y = y; 
[x, y] 
```




