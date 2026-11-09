# EXP-XXX: <Short descriptive title>

| Field | Value |
|---|---|
| **Status** | Planned / Running / Complete |
| **Verdict** | ✅ Adopt / ❌ Reject / ⚠️ Inconclusive |
| **Focus area** | Retrieval / Context engineering / Performance / Evaluation / Integration |
| **Started** | YYYY-MM-DD |
| **Completed** | YYYY-MM-DD |
| **Related** | Links to research notes, earlier experiments, ADRs |

---

## 1. Problem

What limitation or open question does this address? Why does it matter in a real system?

## 2. Prior work (fill in before writing code)

| Source | Approach | Reported result | Limitation / gap |
|---|---|---|---|
| Paper / repo / framework | | | |

- **Does an existing solution already solve this?** Yes / Partially / No
- **If yes, why run this experiment?** (e.g. reproduce it on our data, test it under production constraints)

## 3. Hypothesis

> If we **<change>**, then **<metric>** will **<improve by roughly X>** compared to **<baseline>**, because **<reasoning>**.

**Success criterion:** the minimum improvement that counts as meaningful, decided in advance.

## 4. Setup

- **Baseline:** configuration being compared against
- **Variant(s):** what changes, and only that
- **Eval set:** name and version from `evals/datasets/`
- **Models:** embedding model, generator LLM, reranker (with versions)
- **Key parameters:** chunk size, top-k, temperature, etc.
- **Runs / seeds:** number of repeats, to measure variance
- **Hardware / environment:**

**How to reproduce:**

```bash
# exact command(s) to rerun this experiment
```

## 5. Results

| Metric | Baseline | Variant | Δ | Variance (±) |
|---|---|---|---|---|
| Recall@k | | | | |
| Faithfulness | | | | |
| p95 latency (ms) | | | | |
| Tokens / query | | | | |
| Cost / 1k queries | | | | |

Charts, failure examples, and raw outputs go in this folder (`results/`).

## 6. Analysis

- What happened, and why?
- Where did the variant win, and where did it lose? (query types, document types)
- Any surprises or confounding factors?

## 7. Verdict

**✅ Adopt / ❌ Reject / ⚠️ Inconclusive**

Reasoning, in one or two sentences, judged against the success criterion from section 3.

## 8. Production notes (if adopted)

- **When to use it:**
- **When not to use it:**
- **Cost / latency tradeoff:**
- **Component path:** `components/...`
- **ADR:** `docs/decisions/...`

## 9. Follow-ups

- [ ] Open questions or next experiments this suggests
