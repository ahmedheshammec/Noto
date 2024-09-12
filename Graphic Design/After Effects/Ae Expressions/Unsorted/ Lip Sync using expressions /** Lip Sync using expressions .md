**if you have a piece of video footage of some cartoon character talking and you want to sync the lips movement to your audio; the first thing you want to do is convert your audio to keyframes by selecting your audio and going to the animation menu // keyframe assistant // convert audio to keyframes, this will create "audio amplitude" layer. after that you must time remap your character footage, now we will add expression to the time remap property, but before we do that we will pick whip the time remap value to "both channel" value of the audio amplitude layer, now we are ready to add our expression: 
> thisComp.layer("Audio Amplitude").effect("Both Channels")("Slider")￼
this will be the expression you'll find as a result of linking the time-remapping value to the "both channels" slider, now what we gonna do is add a variable like this: 
> a=thisComp.layer("Audio Amplitude").effect("Both Channels")("Slider")￼
now go to "both channels" slider and see the minimum and maximum value from the info panel in after effects, 
now get back to the expression we just created and add ease expression like this: 
> a=thisComp.layer("Audio Amplitude").effect("Both Channels")("Slider")
> ease(a,min,max,0,1)￼
that's it, the "::min::" refers to the minimum value, and the "::max::" refers to the max value


