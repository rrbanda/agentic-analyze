# Lyzr vs Hyperscaler Platforms

## The Ecosystem Lock-In Dynamic

Each hyperscaler has shipped an agent platform. All are excellent within their own ecosystem and weak outside it. Lyzr's play is to be the neutral layer above them all.

---

## Comparison Matrix

| Capability | Lyzr | Microsoft Copilot Studio | Salesforce Agentforce | AWS Agent Core | Google Vertex AI |
|-----------|------|-------------------------|----------------------|----------------|-----------------|
| **Multi-framework** | LangChain, CrewAI, Agentforce, Copilot, custom | Microsoft-only | Salesforce-only | AWS-native | Google-native |
| **Multi-cloud** | AWS, Azure, GCP, on-prem | Azure-first | Salesforce Cloud | AWS-only | GCP-only |
| **Multi-model** | OpenAI, Anthropic, Google, open-source | GPT-5, Anthropic, Azure OpenAI | Multiple via Einstein | Bedrock models | Gemini models |
| **MCP Support** | Native | GA (May 2025) | Beta (Oct 2025) | Partial | Partial |
| **A2A Support** | Native (A2A node in SuperFlow) | Partial | None | Partial | Native |
| **Governance (RBAC, audit)** | Full (Control Plane) | Strong within MS stack | Strong within SF stack | Limited governance UI | Emerging (Gemini Enterprise) |
| **Agent Identity** | Okta per agent | Entra ID | Salesforce permissions | IAM | Google IAM |
| **Simulation Engine** | Native (persona x scenario) | None native | None native | None native | None native |
| **Agent CI/CD** | Native Git-triggered pipeline | Power Platform ALM | Salesforce DevOps | CodePipeline integration | Cloud Build integration |
| **Pre-built Agents** | 200+ (Amadeo, Jazon, Skott) | Copilot templates | Agentforce templates | Bedrock agent templates | Vertex agent templates |
| **Pricing** | $0.03-$0.30/run | $30/user/mo + credits | ~$2/conversation | Usage-based | Usage-based |
| **Open Source** | Open-core (Apache 2.0) | Proprietary | Proprietary | Proprietary | Some OSS (ADK) |
| **Requires Rewrite** | No | Yes (to MS format) | Yes (to SF format) | Yes (to AWS format) | Yes (to Google format) |

---

## Head-to-Head Deep Dives

### vs. Microsoft Copilot Studio

**Best for:** Organizations 100% committed to Microsoft 365, Teams, and Azure.

**Strengths:**
- Deepest integration with M365, Teams, Outlook, SharePoint
- 1,400+ Power Platform connectors
- Entra ID for identity management
- Model-agnostic routing (GPT-5, Anthropic, Azure OpenAI)
- Multi-agent orchestration native in Copilot Studio

**Weaknesses:**
- Microsoft-locked. Zero cross-framework support.
- Can't govern LangChain, CrewAI, or custom agents
- No cross-cloud deployment
- Pricing: $30/user/month + Copilot Credits ($200/pack of 25K credits)

**Lyzr's pitch:** "If you're 100% Microsoft, Copilot Studio is fine. But you probably also have LangGraph agents, custom Python scripts, and maybe Agentforce. Lyzr governs all of them."

---

### vs. Salesforce Agentforce

**Best for:** Organizations with Salesforce as their system of record (CRM, Service Cloud, Marketing Cloud).

**Strengths:**
- Native Salesforce data and workflow integration
- Atlas Reasoning Engine
- Trust Layer for model governance
- Outcome-aligned pricing (~$2/conversation)

**Weaknesses:**
- Salesforce-locked. Limited multi-cloud.
- No cross-framework support
- Can't govern agents built outside Salesforce
- MCP support still in beta

**Lyzr's pitch:** "Keep using Agentforce for your CRM agents. Lyzr will govern those AND all your other agents from a single control plane."

---

### vs. AWS Agent Core / Bedrock

**Best for:** AWS-native enterprises.

**Strengths:**
- Deep Bedrock model integration
- AWS-native security (IAM, VPC, KMS)
- Broad model selection
- Scale and reliability

**Weaknesses:**
- AWS-only. No multi-cloud.
- Limited governance UI
- No native simulation engine
- No pre-built vertical agents

**Lyzr's pitch:** "We deploy on AWS. We make your Bedrock agents governable, testable, and auditable."

---

### vs. Google Vertex AI Agent Builder

**Best for:** Google Cloud-native enterprises and teams using A2A protocol.

**Strengths:**
- Native A2A support
- ADK v1.0 with A2A protocol
- Strong AI/ML innovation
- Gemini model access

**Weaknesses:**
- Smaller enterprise footprint than AWS/Azure
- GCP-only deployment
- Less mature governance compared to Microsoft

---

## The Key Pattern

Every hyperscaler platform follows the same pattern:

1. **Excellent within their ecosystem**
2. **Weak outside their ecosystem**
3. **No cross-framework governance**
4. **Requires rewriting agents to their format**

Lyzr's differentiator: **no rewrite required.** Point the Control Plane at your existing repo (LangGraph, CrewAI, custom). It governs what you already have.

For enterprises running 5-7 agent frameworks across multiple clouds -- which describes most Fortune 500 companies in 2026 -- the hyperscaler platforms are necessary but insufficient. The control plane layer is what makes the portfolio manageable.
