# Fikra API

OpenAI-compatible inference API from Nairobi. One `/v1` surface for open-weight models, DeepSeek first: `deepseek-v4.1-flash` at $0.045 per 1M input and $0.09 per 1M output on a 1M context (1017 build $0.05/$0.11, 0731 build $0.045/$0.10, prices verified 2026-10-19). Also GLM 5.3 / 5.3 Flash / 5.2, Kimi K3, StepFun Step 5 preview, Qwen 3.8 27B, MiMo V2.6 Pro, Nemotron 3.5 Super VL, a Gemini 4 Argon route and house lanes.

Billed per token in USD, $1 minimum top-up, M-Pesa and cards.

## Repos

- [deepseek-quickstarts](https://github.com/Fikra-API/deepseek-quickstarts): runnable curl, Python, Node, AI SDK, LiteLLM, CrewAI and DSPy clients
- [awesome-deepseek-compatible-endpoints](https://github.com/Fikra-API/awesome-deepseek-compatible-endpoints): listing of OpenAI-compatible endpoints serving DeepSeek, machine mirror in endpoints.json
- [fikra-benchmark](https://github.com/Fikra-API/fikra-benchmark): nightly lane probes and status
- [anza](https://github.com/Fikra-API/anza): open-source AI SaaS starter (auth, Paystack/Stripe payments, OpenAI-compatible client)

## Endpoints

- Base URL: https://api.fikraapi.co.ke/v1
- Pricing: https://fikraapi.co.ke/pricing
- Docs: https://fikraapi.co.ke/docs

## Surface

Chat Completions ships the OpenAI request surface: `tools`, `tool_choice`, `n`, `seed`, `stop`, `presence_penalty`, `frequency_penalty`, `response_format` (structured JSON output). Reasoning models emit reasoning content; `thinking` and `reasoning_effort` controls are not exposed.
