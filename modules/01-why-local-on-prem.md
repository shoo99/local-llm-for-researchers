# Module 1 — Why local / on-prem at all?

> Part of [Local LLMs for Researchers](https://github.com/shoo99/local-llm-for-researchers).

Before any tokens/sec or quantization tables, one honest question: **should you run the model yourself at all?** For most people, most of the time, a hosted API (the frontier models) is the right answer. This handbook is for the cases where it isn't — and it's worth being clear about which case you're in.

## When local / on-prem genuinely wins

**1. Data governance — the big one.** If your corpus *cannot leave the building* — patient records, unpublished data, IP, anything under a DUA/IRB/NDA or a regulatory regime — a cloud API is simply off the table. No "we don't train on your data" promise changes a contractual or legal *must-stay-on-prem*. This is the reason most of the work in this handbook exists.

**2. Cost at scale.** One question to an API is free-ish. Extracting structured data from 10,000 papers, embedding a million chunks, or running an agent in a loop is not. Past some volume, hardware you already own (even old GPUs, even CPUs) beats per-token billing — and the marginal cost of the next run is electricity, not invoices.

**3. Reproducibility.** A hosted model can change under you — silently, between Tuesday and Wednesday — and your results shift with it. A local GGUF with a pinned version and a fixed seed is *the same model next year*. For anything that feeds a paper, that matters.

**4. Offline / air-gapped / latency.** No internet, no egress, no round-trip. Sometimes that's a security requirement; sometimes it's just a flaky connection on a cluster node.

**5. Control & learning.** You can see the prompts, log every call, swap quantizations, and understand exactly what's happening. You also *learn the stack* — which, if you build research tooling, is its own payoff.

## When it does **not** win (be honest)

- **Capability.** Frontier hosted models are substantially smarter than anything you'll run on a single consumer GPU. If you need the best possible reasoning on a one-off task and the data is shareable — just use the API.
- **Effort.** Local means hardware, drivers, setup, and maintenance. We hit a GPU driver wall, a multimodal crash, and a wedged GPU *while writing this course*. That overhead is real.
- **Speed/quality tradeoffs.** Quantization to fit a budget card costs quality; old hardware is slow. For interactive, high-stakes single queries, that may not be the trade you want.

A quick gut check — **go local when most of these are true:**

- [ ] The data can't (or shouldn't) leave your machine.
- [ ] You'll run *many* calls, not a handful.
- [ ] You need the same model to behave the same way over time.
- [ ] A capable-but-not-frontier model is good enough for the task.
- [ ] You have (or can borrow) a GPU with ≥8 GB, or patience for CPU.

If you ticked three or more, the rest of this handbook is for you. If you ticked zero or one, honestly — open an API tab and get on with your research.

## What the rest of the course does

With that settled, the remaining modules are the practical "how": what fits on your hardware (Module 2), running models and surviving the traps (Module 3), scaling with no GPU (Module 4), building a **private assistant over your own papers** (Module 5, the capstone), and — crucially — **checking whether the thing is actually good enough for your field** (Module 6).

→ Next: **[Module 2 — The hardware reality](https://bric.pe.kr/blog/qwen3-6-35b-a3b-2x-1080-ti-benchmark-2026)**
