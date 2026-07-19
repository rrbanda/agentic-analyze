# Executive Summary

## The Bottom Line

**Lyzr has built the business model that enterprise customers are signaling they want for agentic AI: a framework-agnostic control plane with consumption-based pricing, sovereign deployment, and production-grade governance.** Their platform is more mature at the app layer (Agent Studio, Architect, pre-built agents) and is rapidly closing the gap at the infrastructure layer (Control Plane, CI/CD, Okta identity per agent).

---

## What Lyzr Is

Lyzr.ai is a **full-stack enterprise agent infrastructure platform** founded in 2023 by Siva Surendira (previously built PowerUpCloud, acquired by L&T Infotech in 2019). The company has raised **$125M total** at a **$500M valuation** (Series B, July 2026) and claims **1,000+ agents live in production across 500+ enterprise customers**.

Their core product is the **Lyzr Agent Control Plane** -- a governance layer that sits *above* agent execution frameworks. It accepts agents built on LangChain, CrewAI, Agentforce, Copilot, or any custom code, and adds:

- **Identity** (Okta per agent), **RBAC**, and **audit trails**
- **CI/CD pipelines** for agents (triggered by Git push, version-tagged, rollback-capable)
- **Simulation Engine** (up to 10,000 synthetic test runs before production)
- **Responsible AI** (PII redaction, hallucination management, toxicity controls)
- **Observability** (traces, latency, token usage, cost tracking)

---

## Why Customers Want This

The agentic AI market has a massive **ambition-to-execution gap**:

- **83-93%** of organizations plan to deploy agents
- **Only 23%** are actually scaling them
- **89%** of agent projects never reach production
- **40%+** of agentic AI projects will be cancelled by 2027 (Gartner)

Enterprises don't fail because their agents are bad. They fail because they lack **governance, testing, identity management, CI/CD, and observability** for agents. Lyzr sells the solution to that exact problem.

---

## The Competitive Threat

Lyzr's positioning is strategically dangerous because:

1. **They don't compete with frameworks -- they govern them.** A customer using LangGraph or CrewAI on RHOAI could add Lyzr's Control Plane on top without changing anything. Lyzr becomes the management layer.

2. **They're cloud-agnostic and framework-agnostic.** They run on AWS, Azure, GCP, on-prem, and air-gapped. This directly overlaps with the multi-cloud value proposition.

3. **Their pricing aligns with value.** $0.03-$0.30 per agent run vs. seat-based pricing. Customers pay for what runs, not for what's installed.

4. **They have vertical solutions.** Amadeo (banking), Jazon (sales), Skott (marketing) -- pre-built agent suites that show immediate ROI. A KYC workflow costs ~$1.02/run vs. thousands in human labor.

5. **They're backed by Accenture and In-Q-Tel.** This gives them enterprise sales channels (Accenture) and government credibility (In-Q-Tel = US intelligence community VC).

---

## Where We Can Compete

| Our Advantage | Why It Matters |
|---------------|---------------|
| **Infrastructure layer** | Kubernetes, GPU scheduling, model serving, Kueue -- Lyzr has *no* infrastructure story. They run *on top of* clouds. |
| **Open source credibility** | Lyzr is "open-core" (Apache 2.0 framework, proprietary enterprise features). We have genuine open-source DNA. |
| **Model training and fine-tuning** | Lyzr's thesis is "context engineering > model selection." But enterprises doing custom model training need infrastructure Lyzr doesn't provide. |
| **MLOps pipeline** | Training -> evaluation -> model registry -> serving -> monitoring. Lyzr starts *after* the model exists. |
| **Hardware optimization** | GPU allocation, multi-model serving, NVIDIA/AMD support. Lyzr is model-agnostic but hardware-unaware. |
| **Hybrid cloud** | OpenShift runs identically on-prem, cloud, and edge. Lyzr supports on-prem but it's not their core strength. |

---

## Recommended Actions

1. **Build or partner for a Control Plane.** The governance layer for agents (identity, CI/CD, audit, simulation) is a real gap. If we don't fill it, Lyzr (or IBM watsonx) will sit on top of our infrastructure and own the customer relationship.

2. **Invest in agent simulation/evaluation.** Lyzr's Simulation Engine (persona x scenario testing, automated hardening) is a genuine differentiator. LangSmith and Braintrust exist but are framework-specific. A cloud-native, framework-agnostic eval service would be high value.

3. **Develop consumption-based pricing for agentic workloads.** Seat-based or subscription pricing feels wrong for agents. The market is moving to per-run pricing.

4. **Create vertical reference architectures.** Lyzr wins deals with "here's your KYC agent running in 30 days." We need equivalent accelerators for our target verticals.

5. **Position infrastructure as the foundation.** Lyzr needs someone to run their Control Plane on. If that's OpenShift + GPU infrastructure, we're complementary. If they partner with a competing cloud, we're displaced.

---

*See [Competitive Response Playbook](strategic/competitive-response.md) for detailed tactical recommendations.*
