if you have a property let's say scale or opacity and it's keyframed on the timeline and you don't want to mess up the keyframes, you just want the value to be reduced by 50% you can do that by adding an expression: 
```plaintext
value-50
```
which will decrease the value by 50 points; you can also apply all kinds of operations on the value like adding, subtraction, etc.
but what if you are working with something like a position that has 3 values: x y z, in that case, we will use an array like this: 
```plaintext
[value[0],value[1],value[2]]
```
and now we can build upon that like adding values the current value: 
```plaintext
[value[0]-50,value[1]+70,value[2]*2]
```
but guessing the right number for x and y values can be inconvenient so we take this up a notch and use slider control for x and y values, add two slider control effects and rename them to X and Y, now in the expression instead of specifing the value manually pick whip the value to the slider so it will look something like this: 
```plaintext
[value[0]+effect("X")("Slider"), value[1]+effect("Y")("Slider")]
```
now you can easily get the right value without trying to guess it. 


