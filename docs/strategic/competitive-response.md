# Competitive Response Playbook

!!! tip "Action-Oriented"
    This page translates analysis into specific, prioritized actions for competing with Lyzr's business model.

---

## The Core Problem

Lyzr has built the **full-stack agent platform that enterprise customers are asking for**: build, test, deploy, govern, observe. They sit above the infrastructure layer and own the customer conversation about AI agents.

Our strength is in the **infrastructure layer**: Kubernetes, GPU scheduling, model serving, model training. But without an agent management story, we risk being commoditized infrastructure beneath someone else's control plane.

---

## Strategic Options

### Option A: Build a Control Plane (Build)

Build an open-source agent control plane that integrates with OpenShift.

**Pros:**

- Own the full stack (infrastructure + governance)
- Open-source disruption of Lyzr's proprietary model
- Consistent with Red Hat's DNA
- Strongest long-term competitive position

**Cons:**

- 12-18 months to minimum viable product
- Requires investment in new capabilities (agent identity, CI/CD for agents, simulation)
- Risk of building something customers don't want
- Distraction from core infrastructure focus

**Recommendation:** Start here with focused investment. An open-source agent control plane is the highest-impact response.

---

### Option B: Partner with Lyzr or Similar (Partner)

Establish a partnership where Lyzr's control plane runs natively on OpenShift.

**Pros:**

- Immediate capability (no build time)
- Validates the stack: "Lyzr agents on OpenShift infrastructure"
- Revenue opportunity from infrastructure consumption
- Access to Lyzr's enterprise customers

**Cons:**

- Lyzr owns the customer relationship
- Revenue uplift is limited (infrastructure margin, not agent management margin)
- Lyzr could partner with any cloud -- no exclusivity
- Commoditizes our platform

**Recommendation:** Pursue as a bridge strategy while building Option A. Don't make it exclusive.

---

### Option C: Extend Existing Tools (Evolve)

Add agent-specific capabilities to existing RHOAI components.

**Pros:**

- Incremental investment
- Builds on existing product strengths
- Lower execution risk

**Cons:**

- May not be compelling enough against purpose-built platforms
- Risk of "good enough" that doesn't win deals
- Doesn't address the governance gap at the right abstraction level

**Recommendation:** Do this regardless, as a foundation for Option A. But don't rely on it alone.

---

## Tactical Recommendations (Prioritized)

### Phase 1: Foundation (0-6 Months)

#### 1.1 Agent Registry on OpenShift

Build an open-source agent registry that tracks deployed agents across frameworks.

| Feature | Detail |
|---------|--------|
| Registry data model | Framework, runtime, deployment status, owner, version |
| Multi-framework support | LangGraph, CrewAI, custom agents |
| API-first | REST/gRPC API for registration and discovery |
| OpenShift integration | CRDs for agent resources on Kubernetes |
| Observability | Prometheus metrics, OpenTelemetry traces |

**Why first:** The registry is the "etcd" of agent governance. Everything else builds on it.

#### 1.2 Agent Observability

Extend existing monitoring to agent-specific metrics:

- Per-agent traces (input, output, latency, tokens, cost)
- Hallucination rate tracking
- Tool call success/failure rates
- Cost attribution per agent and per team

**Build on:** Existing Prometheus/Grafana/OpenTelemetry stack in OpenShift.

#### 1.3 Agent CI/CD via GitOps

Extend OpenShift GitOps (ArgoCD) for agent deployment:

- Agent-specific deployment pipelines
- Evaluation gates before production promotion
- Version tagging and rollback
- Integration with existing CI/CD workflows

**Build on:** Existing ArgoCD/Tekton capabilities.

---

### Phase 2: Differentiation (6-12 Months)

#### 2.1 Agent Simulation Service

Cloud-native, framework-agnostic agent evaluation service:

- Persona x scenario test generation
- Multi-turn evaluation
- Automated failure analysis
- Integration with Phase 1 CI/CD (evaluation gates)

**Differentiate from Lyzr:** Open-source, runs on customer's infrastructure, no platform dependency.

#### 2.2 Agent Identity via Keycloak/RHSSO

Per-agent identity management using existing Red Hat SSO infrastructure:

- Dedicated service accounts per agent
- RBAC for agent capabilities
- Audit logging of agent actions
- Automatic credential rotation and revocation

**Differentiate from Lyzr:** Uses customer's existing identity infrastructure instead of requiring Okta.

#### 2.3 Vertical Reference Architectures

"Deploy a KYC agent on OpenShift in 30 days":

- Banking: KYC, loan origination, compliance monitoring
- Healthcare: Clinical decision support, claims processing
- Telecom: Network operations, customer service
- Government: Regulatory compliance, citizen services

**Build on:** Partner with ISVs or build internally. Each reference arch includes the agent pattern, knowledge base setup, and governance configuration.

---

### Phase 3: Platform Play (12-18 Months)

#### 3.1 Open-Source Agent Control Plane

Combine Phase 1 and Phase 2 components into a unified, open-source agent control plane:

- Agent Registry (Phase 1.1)
- Agent Observability (Phase 1.2)
- Agent CI/CD (Phase 1.3)
- Agent Simulation (Phase 2.1)
- Agent Identity (Phase 2.2)
- Governance policies (RBAC, audit, compliance)

**Name suggestion:** "AgentShift" or "OpenAgent" -- needs to be memorable and clearly positioned.

**Differentiate from Lyzr:**

| Dimension | Our Control Plane | Lyzr |
|-----------|------------------|------|
| Licensing | Open source | Open-core (proprietary enterprise) |
| Infrastructure | Runs on YOUR OpenShift | Lyzr Cloud or customer VPC |
| Identity | YOUR Keycloak/RHSSO | Okta (external dependency) |
| Cost model | Infrastructure cost only (you own it) | Per-run fee + LLM pass-through |
| GPU/model serving | Integrated (vLLM, KServe) | Not available |
| Model training | Integrated (InstructLab, distributed training) | ShadowLM (emerging) |
| Vendor lock-in | None (open source) | Moderate (Lyzr platform dependency) |

#### 3.2 Consumption-Based Metering

Add per-agent-run metering to OpenShift:

- Track agent invocations, token usage, compute consumed
- Enable consumption-based billing for managed service customers
- Cost attribution and chargeback for enterprise teams

---

## Quick Wins (Can Start Immediately)

1. **Publish agent deployment patterns on OpenShift** -- blog posts, reference architectures showing LangGraph + CrewAI on OpenShift
2. **Create an "Agents on OpenShift" demo** -- demonstrate multi-framework agent deployment with observability
3. **Engage with AAIF** -- Participate in Linux Foundation Agentic AI Foundation governance discussions
4. **Evaluate Lyzr's ADK** -- Install `lyzr-adk`, build test agents, document the experience for internal teams
5. **Map customer conversations** -- Identify which enterprise customers are evaluating Lyzr or similar platforms

---

## What NOT to Do

1. **Don't build a no-code agent builder (yet).** Agent Studio/Architect are impressive but not our DNA. Focus on infrastructure + governance first.
2. **Don't try to match Lyzr feature-for-feature.** We win by being open-source, infrastructure-native, and vendor-neutral -- not by copying their app layer.
3. **Don't ignore the threat.** "They're just an app layer company" misses the point. The control plane layer is strategically above us.
4. **Don't wait for standards to settle.** Lyzr is shipping governance NOW. Standards are 2-3 years away. Move now.
