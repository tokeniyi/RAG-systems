# RAG-systems

**Research-driven RAG engineering:** studying existing retrieval and context techniques, benchmarking improvements, and turning validated findings into production-ready components for AI agents.

> This is not another RAG tutorial or demo app. It is a working lab: every technique here is researched first, measured against a baseline, and only then turned into reusable code.

---

## Guiding principle: research before implementation

Before building any technique, optimization, or feature:

1. **Survey what exists:** papers, open-source implementations, frameworks, and production practice.
2. **Reuse what already works.** If a solid solution exists, understand it, evaluate it, and integrate it instead of rebuilding it.
3. **Improve only where there's a measured gap.** Where existing approaches fall short, form a hypothesis, test it, and measure whether the improvement actually matters.

Popularity is not evidence. Benchmarks are.

---

## The three pillars

| Pillar | Purpose | Output | Definition of done |
|---|---|---|---|
| **1. Research** | Understand what exists and identify unresolved problems | Paper notes, technique surveys, gap analyses | We can state what exists, how well it works, and what remains unsolved |
| **2. Experimentation** | Implement or adapt techniques, benchmark them, and validate improvements | Experiment records, benchmark results | The result is reproducible and measured against a baseline on a fixed eval set |
| **3. Production** | Turn validated findings into reusable components | Modules, integration patterns, decision records | It can be dropped into an agent or app with known quality, latency, and cost tradeoffs |

### The pipeline

```
Research ──► Hypothesis ──► Experiment ──► Verdict ──► Component
   ▲                                          │
   └──────── rejected / inconclusive ─────────┘
```

**Rule:** nothing enters `components/` without an experiment record in `experiments/` that justifies it.

---

## Focus areas

- **Retrieval techniques:** dense, sparse, and hybrid search; reranking; query rewriting; multi-hop and graph-based retrieval.
- **Context engineering:** how information is selected, filtered, compressed, ordered, and delivered to the model.
- **Performance and token optimization:** latency, cost, resource efficiency, and scalability.
- **Evaluation:** repeatable benchmarks for objective comparison of techniques and architectures.
- **Production integration:** patterns for using these techniques in real AI agents and existing applications.

---

## Repository structure

```
RAG-systems/
├── research/            # Pillar 1
│   ├── papers/          #   one note per paper or technique
│   └── open-problems.md #   known limitations worth investigating
├── experiments/         # Pillar 2
│   ├── _template.md     #   copy this for every new experiment
│   └── EXP-001-<slug>/  #   one folder per experiment
├── evals/               # Shared by every experiment
│   ├── datasets/        #   fixed, versioned eval sets
│   ├── metrics/         #   retrieval and generation metrics
│   └── harness/         #   runner that produces comparable results
├── components/          # Pillar 3: validated, reusable modules only
└── docs/
    ├── decisions/       #   ADRs: why X over Y, and when to use each
    └── findings.md      #   running log: what works, what doesn't, why
```

---

## Evaluation standards

Every experiment must report against the same harness so results are comparable.

| Category | Example metrics |
|---|---|
| Retrieval quality | Recall@k, MRR, nDCG |
| Generation quality | Faithfulness, answer relevance, context precision |
| Efficiency | p50/p95 latency, tokens per query, cost per 1k queries |
| Robustness | Performance on out-of-domain and adversarial queries |

Baselines are fixed per eval set and versioned. A change counts as an improvement only if it beats the baseline by a margin larger than run-to-run variance.

---

## Experiment verdicts

Every experiment ends with exactly one verdict:

- ✅ **Adopt:** a meaningful, reproducible improvement. Promote it to `components/` and record an ADR.
- ❌ **Reject:** no meaningful improvement, or the cost outweighs the gain. Record why.
- ⚠️ **Inconclusive:** mixed or noisy results. Note what would resolve it.

Negative results are first-class findings. Knowing what *doesn't* work, and why, is part of the knowledge base.

---

## Findings index

| ID | Technique | Verdict | Key result | Link |
|---|---|---|---|---|
| EXP-001 | _e.g. Hybrid BM25 + dense retrieval_ | — | — | [→](experiments/) |

See [`docs/findings.md`](docs/findings.md) for the full narrative log.

---

## Roadmap

- [ ] Build the eval harness and a first fixed eval set
- [ ] Establish a naive RAG baseline (fixed chunking + dense retrieval)
- [ ] Survey and benchmark chunking strategies
- [ ] Hybrid retrieval and reranking experiments
- [ ] Context compression and ordering experiments
- [ ] First production component and integration example in an agent

---

## Contributing / working notes

1. Starting something new? Check `research/` and `docs/findings.md` first. It may already be answered.
2. Copy `experiments/_template.md` into a new `EXP-XXX-<slug>/` folder.
3. Fill in the hypothesis and prior work **before** writing code.
4. Run on the shared harness, record a verdict, and update the findings index.
