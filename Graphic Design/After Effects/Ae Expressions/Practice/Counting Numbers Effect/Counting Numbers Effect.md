* start by clicking anywhere with the type tool to get "Empty Text" layer
* Twirl down the "Empty Text" Layer to get to the source text
* Option Click on the stop watch to add an Expression, and add this: 
```plaintext
beginCount = 0;
stopCount = 92;
beginTime = 0; // start counting at time = 1
countDur = 1; // count for 2 seconds
"" + Math.round(linear(time,beginTime,beginTime + countDur,beginCount,stopCount)) + "%"

```
+ "%" is just to add percentage to the text, you can replace it, or even remove it if you like
 beginCount is the value which the counting will start with
stopCount is the value which the counting will stop at
 countDur is the duration of the counting in seconds

