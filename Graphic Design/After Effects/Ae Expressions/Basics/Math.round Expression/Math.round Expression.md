if you have a number like this 155.51545488 and you want to get rid of the decimals, alt-click your source text to add expressions, press home from your keyboard, and add this expression: 
```plaintext
Math.round(Value)
```
the "value" here represents the date of the numbers, so after adding the expression, delete "value)" and press end from your keyboard to go to the end of your expression and add ")" 
for example, the final expression will be something like this: 
```plaintext
Math.round(transform.position[1])
```


