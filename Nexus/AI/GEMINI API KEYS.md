```
AIzaSyBbttyPZggV_VFOkpze_W5RPP2IqteFkNo
```

```
AIzaSyBKo4gCN6NkNnu3cmzrv-MAdpMSjdeKkPg
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


