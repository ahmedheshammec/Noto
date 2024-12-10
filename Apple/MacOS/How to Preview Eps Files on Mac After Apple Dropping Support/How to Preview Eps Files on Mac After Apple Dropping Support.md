
Open the Terminal at the Directory Which Contains the Eps Files and Paste the Following Command: 

```
find . -type f -name '*.eps' -exec gs -dSAFER -dBATCH -dNOPAUSE -dEPSCrop -sDEVICE=png16m -r600 "-sOutputFile={}.png" {} \;
```

This Command Will Convert All Eps Files to Pngs for Easy and Convenient Preview 