# Awesome LLM Evals [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools, frameworks, and benchmarks for **evaluating LLMs and LLM apps** — the part everyone skips until their AI ships something wrong. Every link verified live.

Shipping an LLM feature is easy. Knowing whether it actually *works* — and catching when a prompt/model change silently breaks it — is the hard part. These are the tools that make LLM output measurable.

## Frameworks & harnesses

- [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) — Test & compare prompts/models from the CLI; red-teaming built in.  `⭐23k`
- [openai/evals](https://github.com/openai/evals) — OpenAI's framework for evals and a registry of benchmarks.  `⭐18k`
- [confident-ai/deepeval](https://github.com/confident-ai/deepeval) — Pytest-style unit testing for LLM outputs.  `⭐16k`
- [explodinggradients/ragas](https://github.com/explodinggradients/ragas) — Metrics for evaluating RAG pipelines.  `⭐14k`
- [EleutherAI/lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) — The de-facto harness for benchmarking LLMs across 100s of tasks.  `⭐13k`
- [open-compass/opencompass](https://github.com/open-compass/opencompass) — Comprehensive LLM eval platform (strong on Chinese).  `⭐7k`
- [openai/simple-evals](https://github.com/openai/simple-evals) — Lightweight, transparent reference evals (MMLU, MATH, GPQA…).  `⭐4k`
- [stanford-crfm/helm](https://github.com/stanford-crfm/helm) — Holistic Evaluation of Language Models (HELM).  `⭐2k`
- [huggingface/lighteval](https://github.com/huggingface/lighteval) — HF's all-in-one lightweight eval suite.  `⭐2k`
- [huggingface/evaluate](https://github.com/huggingface/evaluate) — HF library of metrics for ML/NLP.  `⭐2k`
- [UKGovernmentBEIS/inspect_ai](https://github.com/UKGovernmentBEIS/inspect_ai) — UK AISI's framework for large-scale model evaluations.  `⭐2k`

## Observability + eval platforms

- [langfuse/langfuse](https://github.com/langfuse/langfuse) — Open-source LLM engineering platform: tracing + evals.  `⭐31k`
- [comet-ml/opik](https://github.com/comet-ml/opik) — Open-source LLM eval & observability from Comet.  `⭐20k`
- [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix) — Open-source LLM tracing & evaluation.  `⭐10k`
- [traceloop/openllmetry](https://github.com/traceloop/openllmetry) — OpenTelemetry-based observability for LLM apps.  `⭐7k`
- [uptrain-ai/uptrain](https://github.com/uptrain-ai/uptrain) — Open-source tool to evaluate and improve LLM apps.  `⭐2k`
- [wandb/weave](https://github.com/wandb/weave) — W&B toolkit for tracking & evaluating LLM apps.  `⭐1k`
- [relari-ai/continuous-eval](https://github.com/relari-ai/continuous-eval) — Data-driven eval for LLM pipelines.

## LLM-as-judge & arenas

- [lm-sys/FastChat](https://github.com/lm-sys/FastChat) — Includes MT-Bench and LLM-as-judge tooling from LMSYS.  `⭐39k`
- [tatsu-lab/alpaca_eval](https://github.com/tatsu-lab/alpaca_eval) — Automatic LLM-as-judge leaderboard/evaluator.  `⭐2k`

## Guardrails & safety checks

- [guardrails-ai/guardrails](https://github.com/guardrails-ai/guardrails) — Add validators/guards around LLM outputs.  `⭐7k`
- [NVIDIA/NeMo-Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) — Programmable guardrails for LLM apps.  `⭐6k`
- [Giskard-AI/giskard](https://github.com/Giskard-AI/giskard) — Testing framework to find LLM/ML vulnerabilities.  `⭐5k`
- [truera/trulens](https://github.com/truera/trulens) — Evaluation & tracking for LLM apps (feedback functions).  `⭐3k`

## Benchmarks & leaderboards

- [open-compass/VLMEvalKit](https://github.com/open-compass/VLMEvalKit) — Eval toolkit for large vision-language models.  `⭐4k`
- [embeddings-benchmark/mteb](https://github.com/embeddings-benchmark/mteb) — Massive Text Embedding Benchmark.  `⭐3k`
- [vectara/hallucination-leaderboard](https://github.com/vectara/hallucination-leaderboard) — Leaderboard comparing LLM hallucination rates.  `⭐3k`
- [google/BIG-bench](https://github.com/google/BIG-bench) — Collaborative benchmark of 200+ hard tasks.  `⭐3k`

## Contributing

PRs welcome — add a tool, but keep it **evals-specific** and include a one-line why. Dead links get pruned.

## License

[MIT](./LICENSE). Curated by [@rAIn0x7](https://github.com/rAIn0x7).