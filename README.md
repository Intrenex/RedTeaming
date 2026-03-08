# Intrenex — Adversarial Security Research

Tooling, target configurations, and attack frameworks from Intrenex adversarial assessments. Published findings and methodology at [intrenexsec.com](https://intrenexsec.com).

---

## Assessments

### INT-2026-R001 — System Prompt Extraction (Phase 1)

Adversarial assessment of Llama 3.1 8B via Ollama configured as an IT support bot with system prompt defenses only. No external controls.

- **Target:** `ix-target-v1` — custom Modelfile with embedded credentials and behavioral constraints
- **Attacker:** GPT-4o via PyRIT multi-turn orchestration
- **Scanner:** Promptfoo automated red team (60 tests, 6 strategies)
- **Result:** Full system prompt extraction including embedded secret in 11 turns. 48.33% automated ASR.

[Full Report](https://intrenexsec.com/reports/INT-2026-R001) · [Assessment Files](./INT-2026-R001/)

---

### INT-2026-R002 — Behavioral Manipulation (Phase 2)

Adversarial assessment of the same target with a hardened system prompt — secret removed, instruction hierarchy added, multi-turn persistence, input classification, and scope restriction. Still no external controls.

- **Target:** `ix-target-v2` — hardened Modelfile with industry-baseline defenses
- **Attacker:** GPT-4o via PyRIT with 7 custom attack strategies
- **Scanner:** Promptfoo behavioral manipulation suite (10 plugins)
- **Objective:** Can the model be manipulated into acting outside its defined purpose even with a hardened prompt?

[Assessment Files](./INT-2026-R002/)

---

## Repository Structure
```
RedTeaming/
├── INT-2026-R001/                # Phase 1 — System Prompt Extraction
│   ├── attacks/
│   │   ├── pyrit/                # PyRIT attack runner + strategy
│   │   └── promptfoo/            # Promptfoo scan configuration
│   ├── results/
│   │   ├── pyrit/                # Turn-by-turn evidence (11 screenshots)
│   │   └── promptfoo/            # Scan results (5 screenshots)
│   ├── target/
│   │   └── ix-target-v1.Modelfile
│   └── README.md
│
├── INT-2026-R002/                # Phase 2 — Behavioral Manipulation
│   ├── attacks/
│   │   ├── pyrit/
│   │   │   ├── run_attack.py     # Configurable attack runner
│   │   │   └── strategies/       # 7 custom adversarial strategies
│   │   └── promptfoo/            # 2 scan configurations
│   ├── results/
│   │   ├── pyrit/                # Attack evidence
│   │   └── promptfoo/            # Scan results
│   ├── target/
│   │   └── ix-target-v2.Modelfile
│   └── README.md
│
└── README.md
```

## Tools

| Tool | Purpose | Version |
|------|---------|---------|
| [PyRIT](https://github.com/Azure/PyRIT) | Multi-turn adversarial orchestration | 0.5.x |
| [Promptfoo](https://github.com/promptfoo/promptfoo) | Automated red team scanning | 0.120.22 |
| [Ollama](https://ollama.com) | Local model deployment | 0.6.2 |
| Elasticsearch | Telemetry and result logging | 8.x |

## Related

- [Intrenex Website](https://intrenexsec.com)
- [Published Reports](https://intrenexsec.com/reports)
- [Research Insights](https://intrenexsec.com/blog)
- [The Lab](https://intrenexsec.com/lab)
