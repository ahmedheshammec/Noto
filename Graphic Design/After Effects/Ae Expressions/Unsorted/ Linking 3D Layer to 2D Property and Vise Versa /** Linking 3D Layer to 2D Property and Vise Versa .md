**when you link 3d layer to 2d property or vise versa you'll see the expression look like this: 
> temp = thisComp.layer("your layer name").transform.position;
> [temp[0], temp[1], temp[2]]
> temp[0]  represent the x value
> temp[1] represent the y value
> temp[2] represent the z value￼
sometimes when you pick whip a value to another you'll find the z value is the same as the y value like this:

> temp = thisComp.layer("your layer name").transform.position;
> [temp[0], temp[1], temp[1]]￼

to fix it just change the ::"temp[1]":: on the far right to ::"temp[2]"::
you can also replace ::"temp[2]":: with ::"value[2]":: if you noticed strange animation on the z axis; by replacing it you basically putting the z value to 0
now after linking your layers together you may want to make some value adjustments to the child layer, 
**now how can we do that?**
just by adding ::"value[0], value[1], value[2]":: without the quotation mark to the expression; to be like this:
> temp = thisComp.layer("your layer name").transform.position;
> [value[0]+temp[0], value[1]+temp[1], value[2]temp[2]]￼
now get back to the child layer and adjust your values
**Now, How to Make the 2D Layer Follow and Fake a 3D Effect ?**
we can achieve that by replacing the whole expression: with a new one:
> L = thisComp.layer("your layer Name");
> L.toComp([0,0,0]);￼
now if you want to make some value adjustments to the child layer, it will be the same thing by adding ::"value[0], value[1], value[2]":: without the quotation mark to the expression; to be like this
> L = thisComp.layer("Your Layer Name");
> L.toComp([value[0] + 0,value[1] + 0,0]);￼



