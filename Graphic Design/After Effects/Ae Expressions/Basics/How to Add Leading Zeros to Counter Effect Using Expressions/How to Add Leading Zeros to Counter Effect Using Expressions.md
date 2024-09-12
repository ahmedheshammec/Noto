❖ First to Add a Counting Effect You Will Create a New Text Layer and Pickwhip the Source Text to the Slider Control, Now when You Increase the Slider the Counting Happens. 
❖ To Add Leading Zeros at the Start You Can Do It in Two Ways Using Expressions to the Source Text: 
### __First Method__
```plaintext
value = Math.floor(effect("Slider Control")("Slider"));
if (value < 10) {
    "0" + value;
} else {
    value;
}
```
This expression will:
	- Use the value from the Slider Control.
	- If the value is less than 10, it will add a leading zero.
	- If the value is 10 or greater, it will display the value as is.
### __Second Method
__```plaintext
value = Math.floor(effect("Slider Control")("Slider"));
value.toString().padStart(4, '0');
```
This expression will:
	- Convert the value from the Slider Control to an integer.
	- Convert the number to a string and pad it with leading zeros to ensure it has four digits.