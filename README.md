# 🪶 Feather AI API (Updated)

**Endpoint:**  
https://feather.loca.lt/api/generate

> Ignore the browser warning from LocalTunnel — the API works normally.

---

## ⚡ Features
- No API key required  
- No rate limits  
- Fast local inference via Ollama  

---

## Available Models
```
llama3.2:1b
llava-llama3:latest
```

---

## Request

**Method:** POST  
**Content-Type:** application/json

### Body
```json
{
  "model": "llama3.2:1b",
  "prompt": "Write a story about space",
  "stream": false
}
```

---

## Response

```python
{
  'model': 'llama3.2:1b',
  'created_at': '2026-03-18T04:49:17.7032948Z',
  'response': 'In the year 2254, humanity had finally reached for the stars. The world was in the midst of a great migration…',
  'done': True,
  'done_reason': 'stop',
  'context': [ … ],
  'total_duration': 7898714000,
  'load_duration': 2758014200,
  'prompt_eval_count': 30,
  'prompt_eval_duration': 14499900,
  'eval_count': 655,
  'eval_duration': 4737309300
}
```

---

## Python

```python
import requests

url = "https://feather.loca.lt/api/generate"

payload = {
    "model": "llama3.2:1b",
    "prompt": "Write a story about space",
    "stream": False
}

res = requests.post(url, json=payload)
data = res.json()

print("Model:", data['model'])
print("Created at:", data['created_at'])
print("Response:", data['response'])
print("Done:", data['done'])
```

---

## ⚠️ Important
- Only the listed models are supported; any other model will error.  
- These models can produce unreliable or nonsensical outputs. For better results, combine them with a web search or external knowledge source.
