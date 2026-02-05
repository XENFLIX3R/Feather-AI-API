# Feather AI API

**Endpoint:** https://feather.loca.lt/generate  

> ⚠️ When opening the link in a browser, LocalTunnel may show a warning. You can safely ignore it. The API works normally.  

- **No API key required**  
- **No rate limits**  
- **Supports multiple models**  

---

## Request Format

**Method:** `POST`  
**Content-Type:** `application/json`  

**Body:**

```json
{
  "model": "llama3.2:1b",
  "prompt": "Hello, how are you?"
}
```

---

## Response Format

```json
{
  "Model": "llama3.2:1b",
  "Time": "25ms",
  "Response": "Hello, how can I assist you?"
}
```

---

## Example Usage

### Python

```python
import requests
import json

url = "https://feather.loca.lt/generate"

payload = {
  "model": "llama3.2:1b",
  "prompt": "Hello, how are you?"
}

response = requests.post(url, json=payload)
data = response.json()

print("Model:", data["Model"])
print("Time:", data["Time"])
print("Response:", data["Response"])
```

---

### JavaScript (Node.js)

```javascript
import fetch from "node-fetch";

const url = "https://feather.loca.lt/generate";

const payload = {
  model: "llama3.2:1b",
  prompt: "Hello, how are you?"
};

const res = await fetch(url, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(payload)
});

const data = await res.json();
console.log("Model:", data.Model);
console.log("Time:", data.Time);
console.log("Response:", data.Response);
```

---

### Lune/Lua

```lua
local serde = require("@lune/serde")
local net = require("@lune/net")

local function requestAI(prompt: string, model: string?)
    model = model or "llama3.2:1b"

    local response = net.request({
        url = "https://feather.loca.lt/generate",
        method = "POST",
        headers = { ["Content-Type"] = "application/json" },
        body = serde.encode("json", { prompt = prompt, model = model })
    })

    if not response.ok then
        return `Error: {response.statusCode} - {response.body}`
    end

    local decoded = serde.decode("json", response.body)
    return decoded
end

local result = requestAI("Hello, how are you?", "llama3.2:1b")
print("Model:", result.Model)
print("Time:", result.Time)
print("Response:", result.Response)
```
