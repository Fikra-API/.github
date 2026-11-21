# Fikra API

OpenAI-compatible inference API and coding agent, built in Nairobi. One `/v1` surface for DeepSeek, Qwen, Gemini, Kimi, GLM and Fikra models. Pay by card or M-Pesa.

## Fikra Code

A coding agent that runs well on the laptop you already own. Gemini, DeepSeek, Qwen, Kimi and GLM in one plan, from $10 a month or KES 200 a week.

```sh
curl -fsSL https://fikraapi.co.ke/code/install.sh | sh   # Linux
irm https://fikraapi.co.ke/code/install.ps1 | iex        # Windows PowerShell
fikra                                                    # signs in through your browser
```

| Plan | Price | Allowance |
| --- | --- | --- |
| Free | $0 | DeepSeek V4.1 Flash: 150 requests every 5 hours, 500 a week |
| Lite | $10 / month | $0.50 every 5 hours, $3 a week, every model |
| Pro | $25 / month | $1.50 every 5 hours, $8 a week, every model |
| Max | $60 / month | $5 every 5 hours, $18 a week, every model |
| Team | $100 / seat / month | Max allowances per seat, one bill |
| Kenya Weekly | KES 200 / week | M-Pesa or card, every model |

[Website](https://fikraapi.co.ke/code) · [Pricing](https://fikraapi.co.ke/code/pricing) · [Docs](https://fikraapi.co.ke/code/docs) · [Repo](https://github.com/Fikra-API/fikra-code)

## Product updates

- **2026-11-21** · Fikra Code v0.1.3: browser sign-in through the plans page, Fikra branding throughout, Fikra-only models, no OpenAI traffic.
- **2026-11-21** · Fikra Code plans: Lite, Pro, Max, Team ($100/seat) and Kenya Weekly (KES 200, M-Pesa). Paying creates your account.
- **2026-11-21** · New Fikra Code site: pricing with limits per model, install, docs, comparisons and changelog at [fikraapi.co.ke/code](https://fikraapi.co.ke/code).
- **2026-11-20** · Fikra Code v0.1.0: first release, Fikra API and the free DeepSeek model by default.

Full Fikra Code history: [changelog](https://fikraapi.co.ke/code/changelog).

## Models

A selection of the catalog. Prices are USD per 1M input / output tokens, checked 2026-11-21. The live list is at [fikraapi.co.ke/pricing](https://fikraapi.co.ke/pricing) and `GET /v1/models`.

| Model | ID | Input / Output | Context |
| --- | --- | --- | --- |
| DeepSeek V4.1 Flash (free window) | `deepseek-v4-1-flash-economy-free` | free | 1M |
| DeepSeek V4.1 Flash | `deepseek-v4.1-flash` | 0.1875 / 0.75 | 1M |
| DeepSeek V4 Pro (pinned) | `deepseek-v4-pro-pinned` | 1.65 / 4.95 | 1M |
| Qwen 3.8 Max (free route) | `qwen3.8-max` | free | 1M |
| Qwen 4 Max | `qwen4-max` | 1.875 / 5.625 | 1M |
| Qwen 3.8 27B | `qwen3.8-27b` | 0.045 / 0.35 | 1M |
| Gemini 4 Argon | `gemini-4-argon` | 2.50 / 12.00 | 1M |
| Gemini 4 Hydrogen | `gemini-4-hydrogen` | 1.875 / 9.375 | 1M |
| Kimi K3 | `kimi-k3` | 2.4375 / 12.1875 | 1.1M |
| GLM 5.3 | `glm-5.3` | 1.225 / 3.85 | 328K |
| GLM 5.3 Flash | `glm-5.3-flash` | 0.1875 / 0.625 | 328K |
| MiMo V2.6 Pro | `mimo-v2.6-pro` | 0.50 / 1.00 | 1M |
| Fikra Auto | `fikra-auto` | 0.045 / 0.35 | 262K |
| Fikra Code 35B | `fikra-code-35b` | 0.045 / 0.33 | 262K |

## API

- Base URL: `https://api.fikraapi.co.ke/v1` (OpenAI-compatible: Chat Completions and Responses)
- Billing: per token in USD from a $1 top-up, by card or M-Pesa
- [Pricing](https://fikraapi.co.ke/pricing) · [Docs](https://fikraapi.co.ke/docs) · [Status](https://fikraapi.co.ke/status)

## Repos

- [fikra-code](https://github.com/Fikra-API/fikra-code): the Fikra Code coding agent (Rust, Apache-2.0)
- [deepseek-quickstarts](https://github.com/Fikra-API/deepseek-quickstarts): runnable curl, Python, Node, AI SDK, LiteLLM, CrewAI and DSPy clients
- [awesome-deepseek-compatible-endpoints](https://github.com/Fikra-API/awesome-deepseek-compatible-endpoints): community list of OpenAI-compatible endpoints serving DeepSeek-family models
- [fikra-benchmark](https://github.com/Fikra-API/fikra-benchmark): nightly latency and quality probes
- [anza](https://github.com/Fikra-API/anza): open-source AI SaaS starter (auth, Paystack/Stripe payments, OpenAI-compatible client)
