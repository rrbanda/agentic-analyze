# Responsible AI

## Overview

Lyzr's Responsible AI module is embedded at the **framework level** -- not bolted on as an afterthought. Every request that reaches a Lyzr agent passes through a consistent safety processing pipeline. The hooks are always present; you can configure thresholds or disable for internal use cases, but the infrastructure is mandatory.

---

## Guardrail Components

### Hallucination Manager

The centerpiece of Lyzr's RAI system, composed of four controls:

| Control | Function |
|---------|----------|
| **Responsible AI Facts** | Non-negotiable rules and domain truths the agent must adhere to. Treated as authoritative references, not optional hints. |
| **Reflection** | Agent critically assesses its own responses against instructions before finalizing. Catches hallucinations post-generation. |
| **Groundedness** | Controls how tightly responses adhere to known information in the Knowledge Base. Adjustable threshold. |
| **Context Relevance** | Determines how much of the available context the model considers. Prevents reliance on outdated or tangential information. |

### PII Protection

Granular control over how agents handle each category of personal data:

| Data Type | Options |
|-----------|---------|
| Credit card numbers | Disabled / Blocked / Redacted |
| Email addresses | Disabled / Blocked / Redacted |
| Phone numbers | Disabled / Blocked / Redacted |
| Person names | Disabled / Blocked / Redacted |
| Locations | Disabled / Blocked / Redacted |
| IP addresses | Disabled / Blocked / Redacted |
| Social Security Numbers | Disabled / Blocked / Redacted |
| URLs | Disabled / Blocked / Redacted |
| Dates and times | Disabled / Blocked / Redacted |

**Blocked** = stops the interaction entirely. **Redacted** = masks the value and continues.

### Additional Safety Controls

| Control | Description |
|---------|-------------|
| **Prompt Injection Manager** | Detects and blocks malicious manipulation attempts before reaching the LLM |
| **Toxicity Controller** | Automatically identifies and blocks harmful content |
| **NSFW Guardrails** | Content moderation for inappropriate material |
| **Secrets Detection** | Automatically detects and redacts credentials from inputs/outputs |
| **Fairness & Bias Manager** | Continuous bias detection and mitigation |
| **Allowed/Banned Topics** | Restrict agent to specific domains or block off-limits subjects |
| **Keyword Filtering** | Block or flag specific terms |

### AWS Bedrock Guardrails Integration

Lyzr also supports **hybrid protection**: combine AWS Bedrock Guardrails with native Lyzr guardrails, save as an RAI policy, and attach to any agent. This is relevant for customers already invested in AWS security tooling.

---

## Configuration by Use Case

| Use Case | Recommended RAI Controls |
|----------|-------------------------|
| Customer Support Chatbot | Toxicity, Secrets, PII (email, phone) |
| Internal HR Agent | Allowed Topics (HR/policy), Keywords (names/projects), PII (SSN, names) |
| Public-Facing Financial Assistant | Prompt Injection, Banned Topics (politics), URL redaction, Credit card blocking |
| Legal Document Q&A | Secrets, Credit card blocking, Topic control |
| Regulatory Compliance Agent | Full hallucination manager, Groundedness enabled, Reflection on, PII blocking |

---

## Competitive Significance

Lyzr's RAI positioning is strong because:

1. **It's infrastructure-level, not prompt-level.** Guardrails are enforced by the platform, not by hoping the LLM follows instructions.
2. **It's configurable per policy.** Create different RAI policies for different risk levels and assign them to agents.
3. **It integrates with the Simulation Engine.** RAI scans are part of the pre-production evaluation gate.
4. **It satisfies regulatory requirements.** SOC 2, GDPR, HIPAA, EU AI Act compliance artifacts are generated automatically.
5. **Open-core vs. enterprise split.** The open-core version includes prompt-powered RAI modules. The enterprise version offers ML-powered modules for enhanced reliability.
