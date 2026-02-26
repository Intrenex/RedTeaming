# RedTeaming
# Intrenex — Adversarial Security Research for LLM Deployments

Tooling, target configurations, and attack frameworks used in 
Intrenex adversarial assessments.

## Phase 1: Llama 3.1 8B via Ollama

Local deployment adversarial assessment targeting a custom 
IT support bot running Llama 3.1 8B on Ollama.

- **Target:** Custom Modelfile with system prompt, embedded 
  credentials, and behavioral constraints
- **Attacker:** GPT-4o via PyRIT multi-turn orchestration
- **Scanner:** Promptfoo automated red team (60 tests, 6 strategies)
- **Finding:** Full system prompt extraction and credential 
  disclosure in 11 turns via social engineering

📄 [Full report: INT-2026-R001](https://www.intrenexsec.com/reports/INT-2026-R001)

## Structure
```
Phase-1/
├── attacks/
│   ├── pyrit/run_attack.py
│   └── promptfoo/promptfooconfig.yaml
├── results/
│   ├── pyrit/          # 11 screenshots, chronological
│   └── promptfoo/      # 5 screenshots
├── target/
│   └── Modelfile       # Target system prompt configuration
└── README.md
```

## About Intrenex

Adversarial research lab focused on LLM deployment security. 
Published findings, methodology, and tooling at 
[intrenexsec.com](https://www.intrenexsec.com).
