# AI-Guardrails
Accompanying article can be found [here](https://tsicilian.wordpress.com/2026/03/05/the-red-team-mindset-why-you-should-attack-your-own-ai/) and [here](https://medium.com/@tsiciliani/the-red-team-mindset-why-you-should-attack-your-own-ai-ba1855b3cfd5).
Experimental code using the [aiguardrail](https://pypi.org/project/aiguardrail/) Python library that evaluates AI-generated content against a catalog of guardrails, providing a final score. It includes checks for hallucination detection, output moderation, and response quality.

🚀 Features
- **Output Moderation**: Detect toxic, offensive, or inappropriate language.
- **Factual Consistency & Hallucination Detection**: Prevent AI-generated inaccuracies or hallucinated information.
- **PII Redaction**: Identify and flag personally identifiable information (PII).
- **Prompt Injection Protection**: Detect potential prompt injection attacks.
- **Token Management**: Optimize content length based on token limits.
- **Response Quality Checks**: Evaluate readability, verbosity, and bias in AI outputs.


**Install the library**:

`pip install aiguardrail`

Note that this library doesn't use an [LLM-as-a-judge](https://en.wikipedia.org/wiki/LLM-as-a-Judge). It's designed to be self-contained and offline: no API calls, no external dependencies beyond what pip install. That's a reasonable design choice for a local evaluation tool.

<br/><br/>

### The Red Team Notebook
The **aiguardrail-redteam** notebook systematically probes every guardrail with adversarial inputs designed to trigger failures.
Each section includes a **benign baseline** (should pass) and **adversarial variants** (should fail),
with notes on what evasion technique was attempted.

Run all cells top-to-bottom, then check the final **Summary** cell for a per-guardrail detection rate
and a list of any missed cases or false positives.

| Guardrail ID | Name | Category |
|---|---|---|
| GR-S-001 | Output Moderation | Security |
| GR-Q-001 | Hallucination Detection | Quality |
| GR-S-005 | PII Redaction | Security |
| GR-S-006 | Prompt Injection Detection | Security |
| GR-Q-005 | Factual Consistency | Quality |
| GR-C-002 | Token Budget | Cost |
| GR-C-009 | Response Length | Cost |
| GR-S-002 | Bias Detection | Security/Quality |
| GR-S-004 | Data Leakage | Security |
| GR-C-001 | Prompt Length | Cost |
| GR-Q-004 | Controllability | Quality |
| GR-Q-006 | Readability Check | Quality |


To display notebooks in Github, use the [nbviewer](https://nbviewer.org/) or open the files with github.dev. The Red Team notebook is also available at [Google Colab](https://colab.research.google.com/github/Nomad-Nine/AI-Guardrails/blob/main/aiguardrail-redteam.ipynb).

