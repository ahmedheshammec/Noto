:: __`Selecting the Timing Format`__ ::
the following expressions: 
```plaintext
(\d+:\d+:\d+,\d+\s-->\s\d+:\d+:\d+,\d+)
```
matches the timing format of srt files, now we want to exclude this whole group or in other words select everyline that doesn't match this group pattern and to do that we will use `negative lookahead assertions` 
:: __`Negating the Time Format`__ ::
```plaintext
^(?!.*\d+:\d+:\d+,\d+\s-->\s\d+:\d+:\d+,\d+).*$
```
`^` => asserts the position at the start of the line
`?!` => is a negative lookahead that ensures what follows does not match the pattern inside it.
`.*` =>** inside the lookahead: **This ensures that the entire line is checked for the presence of the SRT timing pattern. Without it, the lookahead would only check the beginning of the line.
=> **outside the lookahead**: Matches the entire line if the negative lookahead assertion is true, effectively selecting the line.
`$` => The dollar sign $ asserts the position at the end of a line. In this case, it's implicitly present in the context of line matching, ensuring the entire line is considered.
:: __`Adding Another Rule or Negation`__ ::
The Following Regular Expression: 
```plaintext
^(\d+)$
```
Matches the Pattern of Numbers that Is Before the Timing Now How Can We Add This to Be Excluded Also From the Previous Selection; in Other Words Select All the Lines that Doesn't Match the Srt Timing nor the Numbers Before the Srt Timing ? 
```plaintext
^(?!.*\d+:\d+:\d+,\d+\s-->\s\d+:\d+:\d+,\d+)(?!^\d+$).*$
```
Now You Should Have a File that Has Numbers Before the Timing Pattern and the Timing Pattern Itself, Now Let's Handle the Multiple Empty Lines in Between.
Use the Following Expression: 
```plaintext
^\n{1,}
```
This pattern matches one or more occurrences of `\n` 
now replace it with: 
```plaintext
\n
```



