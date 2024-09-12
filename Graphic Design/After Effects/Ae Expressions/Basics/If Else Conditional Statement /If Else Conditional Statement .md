the basic form goes like this: 
```plaintext
if (condition){
	value 1; 
}else{
	value 2;
}
```
for example; if we need to use the If Else Conditional Statement and link it to a checkbox, so that if the checkbox is checked do this and if it's not checked do that. 
to do this in our code we must set a variable for the checkbox first, and reference that variable in our expression.
```plaintext
var checkbox = effect.("checkbox control")("checkbox");
if(checkbox == checked){
	turn the layer on; 
}otherwise{
	turn the layer off;
}
```
note that AE is using the ::==:: which means ::equal:: in Javascript. 
### let's apply this to a layer opacity: 
```plaintext
var checkbox = effect.("checkbox control")("checkbox");
if(checkbox == 1){
	100;
}else{
	0;
}
```
ok that just returns a number value, what if we want it to return a text, for the if Statement to return a text we must use a string by adding the text between double quotes ::"your text"::
### let's apply this to a text layer source text: 
```plaintext
var checkbox = thisComp.layer("Shape Layer 1").effect("On/Off Switch")("Checkbox");
if(checkbox == 1){
	"on";
}else{
	"off"
}
```

### we can also use the if statement to control color, 
and for that, we will use the (color control) effect from the expression controls menu and we will rename it to color one, duplicate it and rename it color 2. 
so now we have two colors (1 & 2), to reference those colors we will make variables: 
```plaintext
var checkbox = thisComp.layer("Shape Layer 1").effect("On/Off Switch")("Checkbox");
var color1 = effect("color 1")("color");
var color2 = effect("color 2")("color");
if(checkbox == 1){
	color1;
}else{
	color2;
}
```
### we can also use greater than & less than with if statement to control some values if other values met certain criteria:
here we are controlling the opacity value by using the if statement which looks at the layer rotation. 
```plaintext
var r = transform.rotation; 
if(r<90){
	100;
}else{
	0;
}
```
 to add ::less than or equal to::, it goes like this: 
```plaintext
var r = transform.rotation; 
if(r<=90){
	100;
}else{
	0;
}
```
to add ::does not equal:: to the expression, it goes like this: 
```plaintext
var r = transform.rotation; 
if(r!=90){
	100;
}else{
	0;
}
```
to expand this a little bit further we can have multiple conditions, and it goes like this: 
```plaintext
var r = transform.rotation; 
if(r<=90 || r>=180){
	100;
}else{
	0;
}
```
the double ::||:: (shift + two forward slashes) = ::or:: in if statement. 
and unlike ::||:: (which means "or") we can say ::and:: like this: 
```plaintext
var r = transform.rotation; 
var s = transform.scale[0];
if(r<=90 && s>=70){
	100;
}else{
	0;
}
```
which means if the rotation is equal to or less than 90 degrees ::and:: the scale is greater than or equal to 70, return opacity value as 100, if not return the value as 0. 
we can also write if statement within if statement like this: 
```plaintext
var r = transform.rotation; 
var s = transform.scale[0];
if(r<=90 && s>=70){
	if(s>=50)}
		50;
	}else{
		25;
	{
}else{
	0;
}
```
please note that if the condition is met it will ignore the rest of the statement. 






