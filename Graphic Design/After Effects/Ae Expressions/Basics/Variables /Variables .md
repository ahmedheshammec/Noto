variables are a very helpful trick you can use all the time to link multiple properties together; so you can say:
```plaintext
a=thisComp.layer("Adjustment Layer 1").effect("offset X ")("Slider");
```
this means that the letter "A" or "The Variable" is referring to a value that we can use later like this: 
```plaintext
position+a
```
this means that we're telling Ae to take the position value and add "a" to it.



