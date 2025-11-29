# AI Experiment Designer Agent (n8n + OpenAI)

A reusable AI Product Management agent that converts any AI feature idea into an **elite, reviewer-grade experiment design doc**:
- crisp hypotheses
- full metric tree with baselines + targets
- offline eval with 4-dimension rubric (correctness, grounding, safety, UX)
- labeling + agreement plan
- robustness coverage axes + stress tests + failure metrics
- online A/B plan with baseline estimates, target lifts, guardrails, cadence, and release gates
- mini eval set + risk/guardrail system
- deterministic doc formatting + email delivery

Built as a modular n8n workflow with strict JSON-first prompting and deterministic formatting.

---
<img width="1218" height="97" alt="image" src="https://github.com/user-attachments/assets/b10e32c7-f720-4130-b678-c72e35436808" />


## Why this exists
Most AI product teams fail at evaluation because plans are:
1) vague, 2) not grounded in baselines, 3) missing safety guardrails, 4) non-portable across domains.

This agent produces a **repeatable, high-signal experiment doc** for any LLM/AI feature in any product domain.

---

## What it generates
A markdown experiment doc with:
1. Title  
2. Problem statement  
3. Target users  
4. Pain points  
5. Jobs-to-be-done  
6. Constraints  
7. Hypotheses (testable, distinct)  
8. Metric tree (baseline + target + target type)  
9. Offline eval plan (rubric + labeling + robustness)  
10. Online experiment plan (A/B + guardrails + gates)  
11. Mini eval test set  
12. Risks & guardrails  

Final output is also beautified for email and sent automatically.

---

## Workflow overview (matches n8n nodes)

### 0) Trigger
**When clicking 'Execute workflow'**  
Manual trigger to run an end-to-end generation.

### 1) Feature Input
**Feature Idea (manual)**  
You paste the feature idea / product context here.

### 2) Clarify
**Clarify (OpenAI)**  
Turns the raw feature idea into structured product spec JSON  
(title, target users, JTBD, constraints, etc).

### 3) Parse Clarify
**Parse Clarify (JS)**  
Extracts strict JSON from the Clarify node (removes markdown / fixes drift).

### 4) Hypotheses + Metrics
**Hypothesis & Metrics (OpenAI)**  
Generates:
- distinct testable hypotheses
- full metric tree with baselines + targets
- AI guardrail metrics (numeric)

### 5) Parse Hypothesis
**Parse Hypothesis (JS)**  
Cleans + parses the hypotheses/metrics JSON.

### 6) Experiment Plan
**Experiment Plan (OpenAI)**  
Creates:
- **offline_eval_plan** with 4-dimension rubric, labeling process, robustness axes, stress tests, per-dimension thresholds  
- **online_experiment_plan** with baseline estimates, target lifts, AI guardrails + cadence, and release gate

Schema-locked and JSON-only.

### 7) Parse Experiment Plan
**Parse Experiment Plan (JS)**  
Sanitizes and parses Experiment Plan JSON.

### 8) Generate Eval
**Generate Eval (OpenAI)**  
Produces a mini eval test set (prompts + expected good outputs + failure modes).

### 9) Parse Eval
**Parse Eval (JS)**  
Parses the mini eval set JSON.

### 10) Generate Risks
**Generate Risks (OpenAI)**  
Outputs:
- Ethical risks
- LLM failure risks
- Data privacy risks
- Edge cases
- Operational guardrails (detect/threshold/action)

### 11) Parse Risks
**Parse Risks (JS)**  
Parses and normalizes risk JSON.

### 12) Format Experiment Doc
**Format Experiment Doc (JS)**  
Deterministically composes one clean markdown document from all nodes.
Handles:
- rubric rendering
- guardrails formatting
- metric baselines/targets/lifts display
- no `[object Object]` leakage

### 13) Beautify Doc for Email
**Beautify Doc for Email (JS)**  
Optional last-mile styling so the doc reads cleanly in email/slack.

### 14) Send a message
**Send a message (Gmail)**  
Emails the final experiment doc automatically.

---
**Feature Idea : 1**: 
We want to add an AI feature inside our health app that helps users understand lab reports. User uploads/opens a report → AI summarizes key abnormalities, explains in simple language, and suggests next steps (doctor consult, lifestyle tips). Constraints: must avoid diagnosis claims, should cite only report data, should handle different report formats.

<img width="547" height="689" alt="image" src="https://github.com/user-attachments/assets/a1a9c61b-94f1-41b8-be3a-380e4a0ca4f8" />


## How to run
1. Import `workflow/n8n-ai-experiment-designer.json` into n8n.
2. Paste your product idea into **Feature Idea (manual)**.
3. Click **Execute workflow**.
4. Final doc appears in **Send a message** output and your inbox.

---

## Design highlights
- **Strict JSON prompts** to eliminate formatting drift.
- **Schema enforced generation** to prevent missing critical fields.
- **Guardrail-first evaluation** (unsupported claims, omissions, policy violations, fallback correctness, latency ceilings).
- **Robustness derived from 4 axes**:
  input variability, user-intent variability, model failure modes, policy/safety risk.
- **Portable across domains** (healthcare example included, but not hard-coded).
- **Deterministic formatter** prevents `[object Object]` or markdown corruption.

---

## Future work
- Add automated rubric scoring via judge models.
- Plug into CI to run mini-eval sets on every model update.
- Add dashboard export for online metrics + guardrails.
