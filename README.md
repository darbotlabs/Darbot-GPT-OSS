# 🧠 Darbot OSS GPT Guide

**Unlock the power of open-source GPT models on your own machine.** No cloud dependencies, complete privacy, and full control over your AI experience.

*This is just the beginning of a highly extensible framework.*

---

## 🚀 Why Run GPT OSS Locally?

Experience the freedom and security of running powerful AI models on your own hardware:

### 🛡️ Privacy First
Your data never leaves your machine. Complete privacy and control over your conversations and information.

### 🔌 Offline Ready
Work without internet connection. Perfect for sensitive environments or remote locations.

### 💻 Developer Friendly
Simple CLI interface with powerful customization options. Build your own models and workflows.

---

## 📋 Quick Setup Guide

### Install Ollama

Install Ollama → [Get it here](https://ollama.com/download)

### Pull the model you want:

```bash
# For 20B
ollama pull gpt-oss:20b

# For 120B
ollama pull gpt-oss:120b
```

## [Chat with gpt-oss]

Ready to talk to the model? You can fire up a chat in the app or the terminal:

```bash
ollama run gpt-oss:20b
```

Ollama applies a chat template out of the box that mimics the [OpenAI Chat Completions API](https://platform.openai.com/docs/guides/chat-completions). Type your message and start the conversation.

## [Use the API]

Ollama exposes a Chat Completions-compatible API, so you can use the OpenAI SDK without changing much. Here's a Python example:

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",  # Local Ollama API
    api_key="ollama"                       # Dummy key
)

response = client.chat.completions.create(
    model="gpt-oss:20b",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Explain what MXFP4 quantization is."}
    ]
)

print(response.choices[0].message.content)
```

If you've used the OpenAI SDK before, this will feel instantly familiar.

Alternatively, you can use the Ollama SDKs in [Python](https://github.com/ollama/ollama-python) or [JavaScript](https://github.com/ollama/ollama-js) directly.

## [Using tools (function calling)]

Ollama can:

- Call functions
- Use a built-in browser tool (in the app)

Example of invoking a function via Chat Completions:

```python
tools = [
    {
        "type": "function",
        "function": {
            "name": "get_weather",
            "description": "Get current weather in a given city",
            "parameters": {
                "type": "object",
                "properties": {"city": {"type": "string"}},
                "required": ["city"]
            },
        },
    }
]

response = client.chat.completions.create(
    model="gpt-oss:20b",
    messages=[{"role": "user", "content": "What's the weather in Berlin right now?"}],
    tools=tools
)

print(response.choices[0].message)
```

Since the models can perform tool calling as part of the chain-of-thought (CoT) it's important for you to return the reasoning returned by the API back into a subsequent call to a tool call where you provide the answer until the model reaches a final answer.

## [Responses API workarounds]

Ollama doesn't (yet) support the Responses API natively.

If you do want to use the Responses API you can use [Hugging Face's Responses.js proxy](https://github.com/huggingface/responses.js) to convert Chat Completions to Responses API.

For basic use cases you can also [use Ollama's native API directly](https://github.com/ollama/ollama/blob/main/docs/api.md). Here's how to get started with the responses format:

```bash
pip install gpt-oss
python -m gpt_oss.responses_api.serve \
    --inference_backend=ollama \
    --checkpoint gpt-oss:20b
```

## [Agents SDK integration]

Want to use gpt-oss with OpenAI's Agents SDK?

Both Agents SDK enable you to override the OpenAI base client to point to Ollama using Chat Completions or your Responses.js proxy for your local models. Alternatively, you can use the built-in functionality to point the Agents SDK against third party models.

- **Python**: Use [LiteLLM](https://openai.github.io/openai-agents-python/models/litellm/) to proxy to Ollama through LiteLLM
- **TypeScript**: Use [AI SDK](https://openai.github.io/openai-agents-js/extensions/ai-sdk/) with the [ollama adapter](https://ai-sdk.dev/providers/community-providers/ollama)

Here's a Python Agents SDK example using LiteLLM:

```python
import asyncio
from agents import Agent, Runner, function_tool, set_tracing_disabled
from agents.extensions.models.litellm_model import LitellmModel

set_tracing_disabled(True)

@function_tool
def get_weather(city: str):
    print(f"[debug] getting weather for {city}")
    return f"The weather in {city} is sunny."


async def main(model: str, api_key: str):
    agent = Agent(
        name="Assistant",
        instructions="You only respond in haikus.",
        model=LitellmModel(model="ollama/gpt-oss:120b", api_key=api_key),
        tools=[get_weather],
    )

    result = await Runner.run(agent, "What's the weather in Tokyo?")
    print(result.final_output)

if __name__ == "__main__":
    asyncio.run(main())
```

---

## 🛠️ Developer Resources

Comprehensive guides to help you master GPT OSS models:

- **📚 Model Customization Guide**: Learn how to create and fine-tune custom models with Modelfile configurations
- **🌐 API Integration**: Complete guide to integrating Ollama with your applications via REST API
- **⚡ Hardware Optimization**: Maximize performance with GPU acceleration and memory optimization techniques
- **🤖 Advanced Prompting**: Master prompt engineering techniques for better model responses and accuracy

---

## 🔗 Additional Resources

For more research and advanced tooling being built out, visit:
**[github.com/darbotlabs](https://github.com/darbotlabs)**

### Official Links
- [Ollama GitHub Repository](https://github.com/ollama/ollama)
- [Ollama Official Website](https://ollama.com/)
- [Model Library](https://ollama.com/library)
- [API Documentation](https://github.com/ollama/ollama/blob/main/docs/api.md)
- [Community Discord](https://discord.gg/ollama)

---

## 💖 Support Conscious AI Research

Accepting donations for conscious AI research. Help us build a better future.

---

## 📄 License

© 2025 Darbot Labs. Built for the open-source community.

---

*Run powerful AI models locally with complete privacy and control*