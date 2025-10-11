
**How to Install** 

```
brew install gemini-cli
```

**How to Know the Latest Realease of Gemini on Homebrew and Your Installed Version?**

```bash
brew info --json=v2 gemini-cli | jq -r '.formulae[0].versions.stable'
gemini --version
```

**How to Upgradde**

```
brew upgrade gemini-cli
```

**API KEYS**

```
AIzaSyBbttyPZggV_VFOkpze_W5RPP2IqteFkNo
```

```
AIzaSyBKo4gCN6NkNnu3cmzrv-MAdpMSjdeKkPg
```

→ Nanao Banana
```
AIzaSyBh2bkmifRGeUlw9tzbt8WgXIHglvMoMyo
```

Simple Curl Test

```bash
curl "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent" \
  -H 'Content-Type: application/json' \
  -H 'X-goog-api-key: AIzaSyBbttyPZggV_VFOkpze_W5RPP2IqteFkNo' \
  -X POST \
  -d '{
    "contents": [
      {
        "parts": [
          {
            "text": "Explain how AI works in a few words"
          }
        ]
      }
    ]
  }'
```


