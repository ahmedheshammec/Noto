**To link one object to another try first to parent your object's layer to the layer which you want to follow, if you want just a single value to link relatively to other layer's value, using expressions is your best bet, but sometimes when you link one value to another both values become the same as the Parent layer value and you don't want that , so to fix this issue try out this expression which uses variables; 
> p = thisComp.layer('NAME OF THE "PARENT" LAYER').transform.position;
> (p.value - p.valueAtTime(0)) + value;￼






