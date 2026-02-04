# HappyCapy AI Gateway 完整信息

## 基础配置

| 项目 | 值 |
|------|-----|
| API 基础 URL | `https://ai-gateway.happycapy.ai/api/v1` |
| API Key 环境变量 | `AI_GATEWAY_API_KEY` (已自动配置) |
| 当前 API Key | `d6175ac7...` (动态获取) |

## 必需的请求头

```python
headers = {
    "Content-Type": "application/json",
    "Authorization": f"Bearer {API_KEY}",
    "Origin": "https://trickle.so",           # 必需！
    "User-Agent": "Mozilla/5.0 (compatible; AI-Gateway-Client/1.0)"  # 必需！
}
```

## 可用端点

### 1. Chat Completions (✅ 可用)

**端点**: `/chat/completions`

**支持的模型**:
- ✅ `gpt-4` - GPT-4 (推荐用于复杂任务)
- ✅ `gpt-4o` - GPT-4 Optimized
- ✅ `gpt-4-turbo` - GPT-4 Turbo
- ✅ `gpt-3.5-turbo` - GPT-3.5 (快速，便宜)
- ❌ `claude-*` - Claude 系列不可用
- ❌ `o1-*` - O1 系列不可用
- ❌ `gemini-*` - Gemini 不可用

**请求格式**:
```python
payload = {
    "model": "gpt-4",
    "messages": [
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "What is 2+2?"}
    ],
    "max_tokens": 50,
    "temperature": 0.7,
    "stream": False  # 支持 streaming
}
```

**响应格式**:
```json
{
  "id": "gen-1770175094-YNKWoDGcjGKFtBECZYha",
  "provider": "OpenAI",
  "model": "openai/gpt-4",
  "object": "chat.completion",
  "created": 1770175094,
  "choices": [
    {
      "finish_reason": "stop",
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "2+2 equals 4."
      }
    }
  ],
  "usage": {
    "prompt_tokens": 24,
    "completion_tokens": 7,
    "total_tokens": 31,
    "cost": 0.00114
  }
}
```

**Streaming 支持**: ✅ 可用
```python
payload["stream"] = True
response = requests.post(url, headers=headers, json=payload, stream=True)
for line in response.iter_lines():
    # 处理 SSE 格式: "data: {...}\n\n"
    pass
```

### 2. Image Generation (⚠️ 部分可用)

**端点**: `/images/generations`

**测试结果**:
- ❌ `dall-e-3` - 不可用
- ❌ `dall-e-2` - 不可用
- ❌ `stable-diffusion` - 不可用
- ❌ `flux` - 不可用

**注**: 图片生成端点存在但没有找到可用的模型

### 3. 其他端点

- ❌ `/models` - 不可用
- ❌ `/completions` - 不可用
- ❌ `/embeddings` - 不可用

## Python 示例代码

### 基础调用

```python
import os
import requests

API_KEY = os.environ.get("AI_GATEWAY_API_KEY")
BASE_URL = "https://ai-gateway.happycapy.ai/api/v1"

headers = {
    "Content-Type": "application/json",
    "Authorization": f"Bearer {API_KEY}",
    "Origin": "https://trickle.so",
    "User-Agent": "Mozilla/5.0 (compatible; AI-Gateway-Client/1.0)"
}

payload = {
    "model": "gpt-4",
    "messages": [
        {"role": "user", "content": "Hello!"}
    ],
    "max_tokens": 100
}

response = requests.post(
    f"{BASE_URL}/chat/completions",
    headers=headers,
    json=payload
)

result = response.json()
print(result['choices'][0]['message']['content'])
```

### Streaming 调用

```python
payload = {
    "model": "gpt-4",
    "messages": [{"role": "user", "content": "Tell me a story"}],
    "stream": True
}

response = requests.post(
    f"{BASE_URL}/chat/completions",
    headers=headers,
    json=payload,
    stream=True
)

for line in response.iter_lines():
    if line:
        line_text = line.decode('utf-8')
        if line_text.startswith('data: '):
            data = line_text[6:]  # 去掉 "data: " 前缀
            if data != '[DONE]':
                import json
                chunk = json.loads(data)
                content = chunk['choices'][0]['delta'].get('content', '')
                print(content, end='', flush=True)
```

### 错误处理

```python
try:
    response = requests.post(url, headers=headers, json=payload, timeout=30)
    response.raise_for_status()
    result = response.json()
except requests.exceptions.Timeout:
    print("Request timeout")
except requests.exceptions.HTTPError as e:
    error_data = response.json()
    print(f"HTTP Error: {error_data.get('error', {}).get('message', str(e))}")
except Exception as e:
    print(f"Unexpected error: {e}")
```

## 成本信息

响应中包含成本信息:
```json
"usage": {
  "cost": 0.00114,
  "cost_details": {
    "upstream_inference_cost": 0.00114,
    "upstream_inference_prompt_cost": 0.00072,
    "upstream_inference_completions_cost": 0.00042
  }
}
```

## 注意事项

1. **必须包含 Origin 和 User-Agent**: 缺少这两个头会导致请求失败
2. **模型名称大小写敏感**: 使用小写，如 `gpt-4` 而非 `GPT-4`
3. **Claude 不可用**: 虽然环境变量显示 `ANTHROPIC_MODEL=claude-sonnet-4-5`，但 Claude 模型在 AI Gateway 中不可用
4. **推荐使用 gpt-4**: 最稳定，功能最全面
5. **Timeout 建议**: 设置至少 30 秒超时时间

## 对 Skill Creator 的影响

### 需要修改的部分

1. **不使用 Anthropic SDK**
   ```python
   # ❌ 原来的代码
   from anthropic import Anthropic
   client = Anthropic(api_key=os.environ.get("ANTHROPIC_API_KEY"))

   # ✅ 改用 AI Gateway
   import requests
   API_KEY = os.environ.get("AI_GATEWAY_API_KEY")
   BASE_URL = "https://ai-gateway.happycapy.ai/api/v1"
   ```

2. **修改请求格式**
   ```python
   # ❌ 原来的 Anthropic 格式
   response = client.messages.create(
       model="claude-sonnet-4-5",
       max_tokens=1024,
       messages=[{"role": "user", "content": prompt}]
   )

   # ✅ 改用 OpenAI 兼容格式
   response = requests.post(
       f"{BASE_URL}/chat/completions",
       headers=headers,
       json={
           "model": "gpt-4",
           "messages": [{"role": "user", "content": prompt}],
           "max_tokens": 1024
       }
   )
   ```

3. **修改响应解析**
   ```python
   # ❌ Anthropic 格式
   content = response.content[0].text

   # ✅ OpenAI 格式
   content = response.json()['choices'][0]['message']['content']
   ```

## 测试结果总结

✅ **可用功能**:
- GPT-4 系列模型完全可用
- Streaming 支持正常
- 错误信息清晰
- 成本追踪完整

❌ **不可用功能**:
- Claude 模型
- 图片生成 (端点存在但无可用模型)
- 模型列表查询
- Embeddings

🎯 **推荐配置**:
- 主模型: `gpt-4` (质量最高)
- 备用模型: `gpt-3.5-turbo` (速度快，成本低)
- Timeout: 30 秒
- 错误重试: 3 次
