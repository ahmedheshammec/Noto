### **Expression example: Start or stop wiggle at specific time
**You can use any expression in place of the **wiggle** expression used here, to begin and end the influence of any expression at a specific time.
Apply the following expression to a property to wiggle it beginning at time 2 seconds:
```plaintext
timeToStart = 2;
if (time > timeToStart)
{
 wiggle(3,25);
}
else
{
 value;
}
```
Apply the following expression to a property to stop wiggling it at time 4 seconds:
```plaintext
timeToStop = 4;
if (time > timeToStop)
{
 value;
}
else
{
 wiggle(3,25);
}
```
Apply the following expression to a property to start wiggling it at time 2 seconds and stop wiggling it at time 4 seconds:
```plaintext
timeToStart = 2;
timeToStop = 4;
if ((time > timeToStart) && (time < timeToStop))
{
 wiggle(3,25);
}
else
{
 value;
}
```












