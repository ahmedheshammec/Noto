if you clicked on the default expressions button; and opened property you'll find different loop expression presets; if you choose one like loop out: 
```plaintext
loopOut(type = "cycle", numKeyframes = 0)
```
you can see the type is set to cycle which means that when the animation is over it'll start from the beginning over and over again, however, if we change the type of loop to ping-pong, it'll come up with a different loop effect, it'll reverse the animation back to the beginning after the animation is over 
```plaintext
loopOut(type = "pingpong", numKeyframes = 0)
```
there is one last type of loop animation called "continue" and what it does basically continues the last animation movement and speed till it gets out of the composition
```plaintext
loopOut(type = "continue", numKeyframes = 0)
```



