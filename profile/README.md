# Fikra Research

An AI systems and efficiency lab, built in Nairobi. We make frontier open models run and fine-tune fast on GPUs anyone can access, and we publish everything: kernels, notebooks, benchmarks and papers.

Fikra Research works alongside two products that use what it proves:

- **Fikra API**: one OpenAI-compatible `/v1` surface for DeepSeek, Qwen, Gemini, Kimi, GLM and Fikra models. Pay by card or M-Pesa.
- **Fikra Code**: a coding agent that runs well on the laptop you already own.

## Research

Our thesis: you should not need an H100 cluster to run, evaluate or fine-tune frontier-grade open models. Instead of chasing parameter scale, we work on low-level GPU kernels, memory planning and reproducible systems engineering for modest, widely available hardware.

### Phase 1 (in progress): Inkling 2 Mini on T4 and L4

Thinking Machines Lab's Inkling 2 Mini is a 26.4B looped Mixture-of-Experts model (Apache 2.0). Its experts ship in NVFP4 and MXFP8, formats that free and low-cost GPUs have no hardware for. We are writing open Triton kernels to close that gap:

- FP4-dequant MoE GEMV kernels for T4 (sm75) and L4 (sm89)
- A 16 GB memory planner for hot and cold experts
- Loop-aware execution and a compressed KV cache
- Our own speculative-decoding draft head (the released checkpoint ships without its MTP weights)
- Loop-aware QLoRA fine-tuning

| Target | Goal |
| --- | --- |
| Decode on one L4 | 100+ tok/s |
| Decode on a free Kaggle T4 | 60+ tok/s, inside 16 GB |
| Quality | within about 1 to 2 points of full precision on Fikra Benchmark 500 |
| Context on L4 | 32k+ tokens |
| Fine-tuning | QLoRA on 1x L4 and 2x T4 |
| Reproducibility | one-click Kaggle notebooks for every number |

These are targets, not results. Measured numbers will be published here as they land.

### Phase 2 (planning)

Training our own looped MoE from scratch at a fraction of the usual cost, reusing Phase 1 kernels with low-precision training and distillation.

### Benchmarks

- **Fikra Benchmark 500**: a frozen 500-task evaluation suite (LiveCodeBench, MMLU-Pro, GSM8K, IFEval, BFCL, GPQA-Diamond, FRES). Phase 1 results on Zenodo: [10.5281/zenodo.23078946](https://doi.org/10.5281/zenodo.23078946)

Our work builds on open research from DeepSeek, Moonshot AI, Qwen, Z.ai, ByteDance Seed, Pearl Research, Thinking Machines Lab and Nous Research.

[Research hub](https://fikraapi.co.ke/research)

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

- **2026-11-25** · Fikra Research launched: systems research on running and fine-tuning frontier open models on accessible GPUs. Phase 1 targets Inkling 2 Mini on T4 and L4.
- **2026-11-21** · Fikra Code v0.1.3: browser sign-in through the plans page, Fikra branding throughout, Fikra-only models, no OpenAI traffic.
- **2026-11-21** · Fikra Code plans: Lite, Pro, Max, Team ($100/seat) and Kenya Weekly (KES 200, M-Pesa). Paying creates your account.
- **2026-11-21** · New Fikra Code site: pricing with limits per model, install, docs, comparisons and changelog at [fikraapi.co.ke/code](https://fikraapi.co.ke/code).
- **2026-11-20** · Fikra Code v0.1.0: first release, Fikra API and the free DeepSeek model by default.

Full Fikra Code history: [changelog](https://fikraapi.co.ke/code/changelog).

## Fikra API

- Base URL: `https://api.fikraapi.co.ke/v1` (OpenAI-compatible: Chat Completions and Responses)
- Billing: per token in USD from a $5 top-up, by card or M-Pesa
- [Pricing](https://fikraapi.co.ke/pricing) · [Docs](https://fikraapi.co.ke/docs) · [Status](https://fikraapi.co.ke/status)

### Models

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

## Repos

- [fikra-code](https://github.com/Fikra-API/fikra-code): the Fikra Code coding agent (Rust, Apache-2.0)
- [fikra-benchmark](https://github.com/Fikra-API/fikra-benchmark): Fikra Benchmark 500 manifest and nightly latency and quality probes
- [deepseek-quickstarts](https://github.com/Fikra-API/deepseek-quickstarts): runnable curl, Python, Node, AI SDK, LiteLLM, CrewAI and DSPy clients
- [awesome-deepseek-compatible-endpoints](https://github.com/Fikra-API/awesome-deepseek-compatible-endpoints): community list of OpenAI-compatible endpoints serving DeepSeek-family models
- [anza](https://github.com/Fikra-API/anza): open-source AI SaaS starter (auth, Paystack/Stripe payments, OpenAI-compatible client)
