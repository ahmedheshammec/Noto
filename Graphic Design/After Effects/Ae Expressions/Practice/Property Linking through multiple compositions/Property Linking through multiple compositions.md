if you want for some reason to pre-compose a layer that have some properties linked to another layer, then you'll face an expression error to solve this problem, go to the parent layer, select the property, from edit menu choose: copy with property links or ctrl + alt + c from your keyboard, now get back to the child layer and click paste, you'll notice the phrase 
```plaintext
thiscomp
```
 has changed to 
```plaintext
comp("composition name").layer("layername")
```
 it's naming the composition and the layer it's linked to.

