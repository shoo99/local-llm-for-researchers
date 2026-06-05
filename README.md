# Private AI on Your Own Hardware — Local LLMs for Researchers

A free, honest handbook for running large language models **locally / on-prem** — on modest or old hardware — and using them for real research work.

No cloud APIs required. A lot of quantization. Real benchmarks, real bugs, and a working private assistant you build yourself.

> Written from hands-on experience running 12B–400B models on a pair of 8-year-old GTX 1080 Ti cards and a CPU-only cluster — by [Byeongsoo Kang](https://github.com/shoo99) (multi-omics & ML; [preprints](https://github.com/shoo99)).

## Who this is for

Researchers, scientists, and data-minded engineers who want to run LLMs **on their own machines** — because the data has to stay on-prem (governance), the budget is small, or you just want control — and who'd rather see **honest numbers and failure modes** than a hype reel.

**Prereqs:** comfort with the command line and a little Python. No ML-infra background assumed.

## What you'll be able to do

By the end you can:
- Read the VRAM math and know **what actually runs** on a budget/old GPU (or no GPU).
- Pull and run models with Ollama, and **survive the traps** (multimodal crashes, reasoning models, quantization tradeoffs).
- Scale to bigger models on a **CPU cluster** when you have no GPU.
- **Build a private research assistant** — RAG over your own PDF library, with citations, fully offline.
- **Honestly evaluate** whether a model is good enough *for your field* — not generic benchmarks.

---

## Curriculum

| # | Module | Status |
|---|---|---|
| 1 | **Why local / on-prem at all** — the honest tradeoffs vs cloud APIs (governance, cost, reproducibility) → [read](modules/01-why-local-on-prem.md) | ✅ Live |
| 2 | **The hardware reality** — VRAM math, MoE vs dense, and when a 2nd GPU actually helps → [read](https://bric.pe.kr/blog/qwen3-6-35b-a3b-2x-1080-ti-benchmark-2026) | ✅ Live |
| 3 | **Running models with Ollama (and the gotchas)** — quant choice (Q4 vs Q8), multimodal crashes, reasoning models → [read](https://bric.pe.kr/blog/gemma-4-12b-gtx-1080-ti-q4-vs-q8) | ✅ Live |
| 4 | **Scaling beyond one box: CPU clusters & MoE** — run 35B–400B with no GPU, and the data bugs that matter more than speed → [read](https://bric.pe.kr/blog/gpu-less-cpu-cluster-llm-extraction-10000-papers) | ✅ Live |
| 5 | **Capstone: a private research assistant (RAG over your papers)** — BGE-M3 + Qdrant + a local LLM, fully offline, with citations → [**build it**](https://github.com/shoo99/paper-rag) | ✅ Live |
| 6 | **Honest evaluation: is it good enough for *your* field?** — test on domain questions you already know the answer to (a model can be fluent and confidently wrong) → [see the bioinformatics test](https://bric.pe.kr/blog/gemma-4-12b-gtx-1080-ti-q4-vs-q8) | ✅ Live |

*This is a living handbook — modules marked 🚧 are being written. Star/watch the repo to follow along.*

## How to use it

- New to local LLMs? Go in order (1 → 6).
- Just want to **build the assistant**? Jump to the **Capstone (Module 5)**.
- Each module links a full write-up with real numbers and the exact commands to reproduce.

## Stack used throughout

`Ollama` · `llama.cpp` · GGUF quantization · `BGE-M3` · `Qdrant` · `Python` · single-GPU / multi-GPU / CPU-only inference on consumer hardware (GTX 1080 Ti).

---

## About / contributing

Maintained by [**@shoo99**](https://github.com/shoo99). Found an error or have a hardware result to add? Open an issue or PR.

*Free and open. The goal is the unglamorous, honest knowledge that makes local LLMs actually usable for research — not a sales funnel.*
