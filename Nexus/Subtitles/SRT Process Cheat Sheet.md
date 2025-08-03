→ Replace Parenthesis & Brackets 

---

→ Replace This:

```
<b>
```

and this:

```
</b>
```

→ With Nothing

---

→ Replace This:

```
<i>
```

and this:

```
</i>
```

→ With Nothing

---

→ Replace This:

```
...
```

→ With a Space

→ Then Replace Double Space with One Space

---

→ Replace This:

```
\{(?!\\an\d\})[^}]+\}
```

With Nothing

---

→ Replace This:

```
<font.+">
```

and this:

```
</font>
```

With Nothing.

---

→ Replace This:

```
(\W)( -)
```

and this:

```
(\W)( ـ)
```

and this:

```
(\W)(ـ)
```

→ With This:

```
$1
```

→ And This

```
(\W)(-)(?![->])
```

→ With This:

```
$1
```

---

→ Replace This:

```
^\s
```

→ With Nothing

---

→ Replace This:

```
\s\s
```

→ With  a single Space. 

---
→ Check Engish - Arabic Lines By Matching Only English Words

```
\b[a-zA-Z]+\b
```
