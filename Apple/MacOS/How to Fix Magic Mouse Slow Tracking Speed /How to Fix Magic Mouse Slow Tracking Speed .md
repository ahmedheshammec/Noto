
I’ll put it here for everyone that realized that not even full tracking speed setting in Mouse preferences was enough for them:
Step 1: Open Terminal
Step 2: Copy paste following command: 
```plaintext
defaults write -g com.apple.mouse.scaling -float 8.0
```
Step 3: Restart your mac.
Step 4: Thank me later :)
You can always go back into the Mouse -> Tracking Speed, in fact mine is at like half, yet it is much faster.
NB: if you change the speed again in Mouse settings you will lose this custom setting and it will be “slow” again.
You want to have the final "8.0" somewhere between "5.0" and "10.00"
IMPORTANT: you'll need to restart each time to test the new speed.


