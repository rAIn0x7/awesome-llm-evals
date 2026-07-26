# Awesome LLM Evals [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) [![link-check](https://github.com/rAIn0x7/awesome-llm-evals/actions/workflows/link-check.yml/badge.svg)](https://github.com/rAIn0x7/awesome-llm-evals/actions/workflows/link-check.yml)

> Tools to answer one question: **did my prompt/model change make the output better or worse?** OSS-first, run-it-yourself, evals-only. Links auto-checked in CI — last verified **2026-07**.

**Before:** you tweak a system prompt, eyeball five outputs, ship it, and hear from users that it regressed on the sixth case.
**After:** you keep a test set, run `promptfoo eval` (or `assert` it in pytest with deepeval), and the diff tells you exactly what broke — before you merge.

**TL;DR — jump to your problem:** offline scoring → [Frameworks](#frameworks--harnesses) · online regressions → [Observability](#observability--eval-platforms) · subjective good-vs-bad → [LLM-as-judge](#llm-as-judge--arenas) · jailbreak / injection defense → [Guardrails](#guardrails--safety--red-teaming) · a number to cite → [Benchmarks](#benchmarks--leaderboards).

### What this list is (and how to read it)

~40 tools that are **evals-specific and usable today** — not general LLM frameworks that happen to expose an `eval()`. The point of a list like this isn't the links (you can Google those); it's the two things Google won't give you:

- **"Pick it when…"** — every entry says what it's *actually* for, so you can choose between promptfoo, deepeval, and ragas in ten seconds instead of reading three docs sites.
- **A maintenance signal** — 🟢 actively maintained · 🟡 **no tagged release in the past 12 months _or_ no commit in the past 6 months** (checkable hard line, not a vibe; last hand-checked 2026-07). A 10k-star repo that hasn't shipped in a year will still waste your afternoon; stars alone won't warn you.

Sorted by GitHub stars within each section as a rough adoption proxy — that's the ordering, **not** the recommendation. Star counts are rounded and `n/a` marks entries with no single canonical repo (SaaS-first tools); those sort to the end of their section. Use the "Pick it when" lines to actually decide. This list is OSS-first; closed-source SaaS is noted only where it leads a category (see [the bottom](#closed-source--commercial-for-reference)).

**Who maintains this & why trust it:** one person, [@rAIn0x7](https://github.com/rAIn0x7), in the open — no vendor sponsorships, and SaaS entries are labeled as such so you always know what you're adopting. The 🟢/🟡 status column is re-checked by hand every month; dead links are pruned automatically by the [link-check CI](./.github/workflows/link-check.yml) (badge up top). If a star count or status looks stale, open an issue — it's a bug.

---

## Frameworks & harnesses

These run **offline / pre-ship**: you bring a dataset (or a benchmark) and get scores. Scan the table, then jump to the one that fits.

| Tool | Stars | OSS/SaaS | Lang | Pick it when… | Status |
|---|---|---|---|---|---|
| [promptfoo](https://github.com/promptfoo/promptfoo) | ⭐23k | OSS | TS/Node | you want CLI/CI side-by-side comparison of prompts & models across providers, **with red-teaming built in** | 🟢 |
| [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) | ⭐13k | OSS | Python | you need to **reproduce academic benchmark numbers** (MMLU, HellaSwag…) across 100s of tasks | 🟢 |
| [deepeval](https://github.com/confident-ai/deepeval) | ⭐16k | OSS | Python | you want to **`assert` output quality inside pytest** / your existing test suite | 🟢 |
| [ragas](https://github.com/explodinggradients/ragas) | ⭐14k | OSS | Python | you're evaluating **only a RAG pipeline** (faithfulness, context recall/precision) | 🟢 |
| [openai/evals](https://github.com/openai/evals) | ⭐18k | OSS | Python | you're writing evals in **OpenAI's registry format** | 🟡 |
| [opencompass](https://github.com/open-compass/opencompass) | ⭐7k | OSS | Python | you want broad model benchmarking with **strong Chinese-language coverage** | 🟢 |
| [inspect_ai](https://github.com/UKGovernmentBEIS/inspect_ai) | ⭐2k | OSS | Python | you're building **large-scale or agentic/safety evals** and want a real eval-authoring framework (UK AISI) | 🟢 |
| [helm](https://github.com/stanford-crfm/helm) | ⭐2k | OSS | Python | you want **holistic, multi-metric** academic evaluation across many scenarios (Stanford CRFM) | 🟢 |
| [lighteval](https://github.com/huggingface/lighteval) | ⭐2k | OSS | Python | you want lightweight benchmarking **wired into the HF Hub** | 🟢 |
| [simple-evals](https://github.com/openai/simple-evals) | ⭐4k | OSS | Python | you want **transparent reference implementations** of MMLU/MATH/GPQA to read and copy | 🟡 |
| [promptbench](https://github.com/microsoft/promptbench) | ⭐2k | OSS | Python | you want to **stress-test prompt robustness** / adversarial perturbations (Microsoft) | 🟡 |
| [evaluate](https://github.com/huggingface/evaluate) | ⭐2k | OSS | Python | you just need **standard NLP metrics** (BLEU/ROUGE/…) as a library | 🟡 |

## Observability & eval platforms

Pick these when you need to eval **in production**: trace real traffic, run evals on live or logged data, and catch regressions over time — as opposed to the offline test-suites above.

| Tool | Stars | OSS/SaaS | Pick it when… | Status |
|---|---|---|---|---|
| [langfuse/langfuse](https://github.com/langfuse/langfuse) | ⭐31k | OSS (+SaaS) | you want self-hostable tracing that **doubles as your eval store** | 🟢 |
| [comet-ml/opik](https://github.com/comet-ml/opik) | ⭐20k | OSS (+SaaS) | you want **online + offline evals** with a generous OSS core | 🟢 |
| [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) | ⭐10k | OSS | you live in **notebooks** and want OTEL traces you can eval on the spot | 🟢 |
| [traceloop/openllmetry](https://github.com/traceloop/openllmetry) | ⭐7k | OSS | you **already run OTEL** and want LLM spans in the same pipeline | 🟢 |
| [deepchecks/deepchecks](https://github.com/deepchecks/deepchecks) | ⭐4k | OSS (+SaaS) | you want **continuous validation & property checks**, not just scores | 🟢 |
| [uptrain-ai/uptrain](https://github.com/uptrain-ai/uptrain) | ⭐2k | OSS | you want **pre-built checks** — but confirm cadence first | 🟡 |
| [wandb/weave](https://github.com/wandb/weave) | ⭐1k | OSS (+SaaS) | you're **already on Weights & Biases** | 🟢 |
| [relari-ai/continuous-eval](https://github.com/relari-ai/continuous-eval) | ⭐0.5k | OSS | you want **pipeline-level metrics** for RAG/agent chains (no release since Jan 2025) | 🟡 |
| [Athina AI](https://github.com/athina-ai/athina-evals) | n/a | OSS SDK + SaaS | you want a **library-first eval SDK** with an optional hosted dashboard | 🟢 |
| **Braintrust** ([autoevals](https://github.com/braintrustdata/autoevals) OSS) | n/a | SaaS | you want a **polished hosted playground** and can live with SaaS | 🟢 |

`n/a` = SaaS-first, no single canonical star-ranked repo. Braintrust's `autoevals` scorers are OSS; the platform is SaaS.

## LLM-as-judge & arenas

Pick these when "correct" is **subjective** (helpfulness, tone, preference) and you want a model or a crowd to rank outputs instead of a hard metric.

- [lm-sys/FastChat](https://github.com/lm-sys/FastChat) — Home of **MT-Bench** and LMSYS's LLM-as-judge tooling. **Pick it when** you want the reference MT-Bench judge setup.  `⭐39k` 🟡
- [tatsu-lab/alpaca_eval](https://github.com/tatsu-lab/alpaca_eval) — Automatic LLM-as-judge leaderboard/evaluator. **Pick it when** you want a fast, cheap win-rate vs. a reference model.  `⭐2k` 🟡

## Guardrails & safety / red-teaming

Pick these when the risk is what the model **emits** — jailbreaks, prompt injection, PII, off-policy output — and you need runtime blocking or pre-ship red-teaming, not accuracy scoring.

- [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails) — Validators/guards around LLM I/O. **Pick it when** you want to enforce output schemas/policies at runtime.  `⭐7k` 🟢
- [NVIDIA/NeMo-Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) — Programmable guardrails via a rails DSL. **Pick it when** you want dialog/flow-level control over what the bot may say.  `⭐6k` 🟢
- [Giskard-AI/giskard](https://github.com/Giskard-AI/giskard) — Testing framework that scans for LLM/ML vulnerabilities. **Pick it when** you want automated vulnerability + bias scanning of a model.  `⭐5k` 🟢
- [NVIDIA/garak](https://github.com/NVIDIA/garak) — LLM vulnerability scanner: jailbreak, prompt-injection, toxicity, leakage probes. **Pick it when** you want a `nmap`-style red-team sweep before shipping.  `⭐4k` 🟢
- [truera/trulens](https://github.com/truera/trulens) — Feedback functions for evaluating/tracking LLM apps. **Pick it when** you want programmable feedback metrics on app traces.  `⭐3k` 🟢
- **[Patronus AI](https://github.com/patronus-ai)** — Automated eval + guardrails (hallucination, PII, safety); **SaaS**, with some OSS models/SDK (e.g. the Lynx hallucination detector). **Pick it when** you want managed safety scoring and can use a hosted API.  🟢

## Benchmarks & leaderboards

Pick these when you want a **number to cite** or a public ranking to compare against — not a harness to run your own tests.

- [open-compass/VLMEvalKit](https://github.com/open-compass/VLMEvalKit) — Eval toolkit for large vision-language models. **Pick it when** your model is multimodal.  `⭐4k` 🟢
- [embeddings-benchmark/mteb](https://github.com/embeddings-benchmark/mteb) — Massive Text Embedding Benchmark. **Pick it when** you're choosing/evaluating an embedding model.  `⭐3k` 🟢
- [vectara/hallucination-leaderboard](https://github.com/vectara/hallucination-leaderboard) — Leaderboard comparing LLM hallucination rates. **Pick it when** you need a citable hallucination ranking.  `⭐3k` 🟢
- [google/BIG-bench](https://github.com/google/BIG-bench) — Collaborative benchmark of 200+ hard tasks. **Pick it when** you want historical/reference tasks — note the repo is largely frozen.  `⭐3k` 🟡
- [TIGER-AI-Lab/StructEval](https://github.com/TIGER-AI-Lab/StructEval) — Benchmark for structured-output generation and conversion across 18 text and visual formats, with a [public leaderboard](https://tiger-ai-lab.github.io/StructEval/). **Pick it when** you need citable format-fidelity scores for JSON, YAML, HTML, or React outputs.  `⭐23` 🟢

## Closed-source & commercial (for reference)

This list is OSS-first, so **fully closed** platforms don't get a ranked entry — but you'll meet them in the wild, so here's the honest map:

- **LangSmith** (LangChain) — the default if you're already on LangChain: tracing + evals + datasets. Closed source; free tier, then paid.
- **Humanloop · Vellum · Langtail · Freeplay** — prompt-management + eval SaaS aimed at PM/eng teams.

> Braintrust, Athina, and Patronus appear in the sections above (not here) because each ships **meaningful OSS**; they're explicitly marked **SaaS** so you know what you're adopting.

## Contributing

PRs welcome — but the bar is the two things that make this list worth more than a search:

1. Keep it **evals-specific** (a general LLM framework with one eval helper doesn't qualify).
2. Include a one-line **"Pick it when…"** (the scenario it wins), an **OSS/SaaS** tag, and an honest **🟢/🟡 status**.

Links are checked automatically by the [link-check workflow](./.github/workflows/link-check.yml) on every push — dead links fail CI and get pruned.

## License

[MIT](./LICENSE). Curated by [@rAIn0x7](https://github.com/rAIn0x7).
