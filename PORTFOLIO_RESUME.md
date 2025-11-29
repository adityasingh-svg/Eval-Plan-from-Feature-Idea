# Portfolio + Resume Artefact: AI Experiment Designer Agent

## One-liner positioning
I built an **AI Experiment Designer Agent** (n8n + OpenAI) that turns any LLM/AI feature idea into a complete, elite-level evaluation and rollout plan — with hypotheses, metric trees, offline rubric scoring, robustness stress tests, online A/B guardrails, and deterministic doc generation.

---

## What this project proves about me
### AI Product judgment
- I don’t just ideate AI features — I **define falsifiable hypotheses**, a measurable metric tree, and realistic baselines/targets.
- I can evaluate model quality beyond accuracy (grounding, safety, UX).

### Evaluation rigor
- I enforce a **4-dimension offline rubric** (task correctness, faithfulness, safety, UX).
- I include **labeling processes + kappa agreement**, robustness axes, stress tests, and quantitative failure metrics.
- I define online releases using **numeric guardrails + sampling cadence + explicit release gates**.

### Systems / execution skill
- Built a full multi-node agent workflow in n8n.
- Debugged schema drift + formatting edge cases.
- Added deterministic JS formatting to prevent `[object Object]` breakage.

---

## Portfolio write-up (copy into Notion / site)

### Problem
AI products often ship without rigorous evaluation plans, leading to hallucination risk, safety violations, regressions, and unclear success criteria.

### Goal
Make experiment design for AI features **fast, repeatable, and reviewer-grade** across any product domain.

### Solution
A modular n8n workflow:
1. Clarifies product context into structured JSON.
2. Produces distinct testable hypotheses and a metric tree with baselines and targets.
3. Generates offline evaluation rubric + robustness plan + success thresholds.
4. Designs online A/B test with baseline estimates, target lifts, guardrails, cadence, and release gate.
5. Outputs a deterministic markdown experiment doc and emails it automatically.

### Demo
Input: any AI feature idea  
Output: full experiment doc including offline + online eval, mini eval set, and risk guardrail system.

### Why it’s elite
- Schema-locked JSON prompting avoids missing fields.
- Guardrail-first evaluation prevents unsafe launches.
- Robustness axes derived from input variability, user intent variability, model failure risks, and policy risks.
- Works across domains (healthcare example shown; not domain-locked).

---

## Resume bullets (pick 2–4)

### AI PM angle
- Built a reusable **AI Experiment Designer Agent** (n8n + OpenAI) that transforms AI feature ideas into full evaluation + rollout plans with hypotheses, metric trees, offline rubrics, robustness stress tests, and online A/B guardrails.
- Standardized evaluation across domains by enforcing **strict JSON schemas**, realistic baselines/targets, numeric safety guardrails, sampling cadence, and explicit release gates.
- Designed offline evaluation framework using a **4-dimension rubric** (correctness, grounding, safety, UX) with inter-rater agreement process (Cohen’s κ ≥ 0.7).
- Implemented deterministic JS doc formatting that eliminated schema drift and `[object Object]` formatting failures.

### Builder / technical angle
- Architected an n8n multi-agent pipeline for AI evaluation planning; integrates schema-locked prompting, parsing, and deterministic markdown rendering.
- Reduced evaluation planning time from hours → minutes while increasing rigor through automated robustness axes derivation and release gating.
- Delivered end-to-end healthcare demo incl. mini eval set and operational guardrail system; pipeline is portable to any AI feature domain.

---

## Best role fit / position framing
You can position this project for:
- **AI Product Manager**
- **LLM Product / Evaluation PM**
- **AI Safety / Trust PM**
- **Applied AI Product Engineer**
- **LLM Evals / Experimentation Lead**

---

## Suggested LinkedIn headline
**AI Product Manager | LLM Evaluation & Safety | Built n8n + OpenAI Experiment Designer Agent**

---

## Suggested short “About” paragraph
I build AI products that ship safely at scale. I specialize in turning LLM feature ideas into measurable hypotheses, baseline-anchored metric trees, offline rubric evaluation frameworks, robustness stress tests, and guarded A/B rollouts. Recently I built an AI Experiment Designer Agent in n8n + OpenAI that automates this end-to-end for any AI product domain.
