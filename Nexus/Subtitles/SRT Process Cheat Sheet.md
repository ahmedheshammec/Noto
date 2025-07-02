→ Replace Parenthesis

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
..
```

→ With a Space

→ Then Replace Double Space with One Space

---

→ Replace This:

```
\{.+\}
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