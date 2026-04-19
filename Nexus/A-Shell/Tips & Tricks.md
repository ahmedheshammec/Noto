**How to Delete a Specific Line from .Profile?**

Use This Command: 

```bash
sed -i '' '11d' .profile
```

→ This will delete line number 11 
→ 👉 `d` = delete

**How to Enter EOF Mode**

Use this command: 

```bash
cat << EOF >> .profile
Line 1 
Line 2
# To Exit Press CTRL ⌃ + D 
```

→ If you want to add something after a specific line use `vim` instead. 