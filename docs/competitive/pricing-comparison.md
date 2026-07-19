# Pricing Comparison

## The Business Model Shift

The agentic AI market is moving decisively toward **consumption-based pricing** (pay per agent run) and away from seat-based or subscription-based models. Lyzr is at the forefront of this shift.

---

## Lyzr Pricing Breakdown

### Subscription Tiers (Build-Time Access)

| Plan | Monthly Price | Credits | Agents | Knowledge Bases | Storage | Support |
|------|-------------|---------|--------|----------------|---------|---------|
| Community | Free | 500 | 10 | 5 | 100 MB | Email |
| Starter | $19/mo | 2,000 | 15 | 10 | 100 MB | Email |
| Pro | $99/mo ($79 annual) | 10,000 | 25 | 15 | 1 GB | Email |
| Enterprise | Custom | Unlimited | Unlimited | Unlimited | Custom | 24/7 + 48-hr integration SLA |

### Production Usage (Run-Time Costs)

=== "Lyzr Cloud (Managed)"

    | Agent Type | Price per Run |
    |-----------|--------------|
    | Simple (Single Agent) | $0.06 |
    | Intermediate (Manager Agent) | $0.18 |
    | Complex (SuperFlow) | $0.30 |
    | Voice Agent | $0.09/minute |

=== "Customer VPC / On-Prem"

    | Agent Type | Price per Run |
    |-----------|--------------|
    | Simple (Single Agent) | $0.03 |
    | Intermediate (Manager Agent) | $0.09 |
    | Complex (SuperFlow) | $0.18 |
    | Voice Agent | $0.06/minute |

### Nested Complexity Pricing

| Sub-agents executed | SaaS Price | VPC Price |
|--------------------|-----------|-----------|
| 1-4 | $0.18 | $0.09 |
| 5-8 | $0.36 | $0.18 |
| 9+ | $0.54 | $0.27 |

### Key Pricing Principles

- **LLM costs are pass-through only.** Lyzr does not mark up LLM usage.
- **VPC/on-prem is 50% cheaper** than managed cloud -- incentivizes data sovereignty.
- **No seat taxes.** You pay for what runs, not for who has access.
- **One price covers the full agent stack** -- orchestration, tools, memory, guardrails.

---

## Cross-Platform Pricing Comparison

| Platform | Pricing Model | Approximate Cost | Notes |
|----------|-------------|-----------------|-------|
| **Lyzr** | Per-run consumption | $0.03-$0.30/run + LLM pass-through | VPC cheaper than cloud |
| **Salesforce Agentforce** | Per-conversation | ~$2/conversation | Also per-agent licensing tiers |
| **Microsoft Copilot Studio** | Per-user + credits | $30/user/mo + $200/25K credits | Bundled with M365 Copilot |
| **IBM watsonx Orchestrate** | Subscription + usage | ~$530/month base + usage | Enterprise implementation required |
| **AWS Bedrock Agents** | Per-invocation | ~$0.01-0.10/invocation + model costs | Infrastructure costs separate |
| **LangGraph Cloud** | Per-run | $0.005/step + infrastructure | Developer-focused |
| **CrewAI Enterprise** | Subscription | Custom | Framework-specific |

---

## The $1.02 KYC Benchmark

Lyzr publishes a detailed benchmark: a full KYC processing workflow for corporate banking customers:

| Component | Detail |
|-----------|--------|
| Agents involved | 20+ |
| Per-run cost | $0.03 (VPC) |
| Total cost per KYC run | $1.02 |
| Equivalent human labor cost | Significantly higher |
| Claimed savings | **Up to 95% lower than human labor** |

This is a powerful sales tool. When a bank can see "$1.02 per KYC run" vs. "$50-100 per manual KYC review," the ROI argument writes itself.

---

## Business Model Analysis

### Why Consumption Pricing Wins

1. **Aligns cost with value.** Customer pays when agents do work, not for idle capacity.
2. **Low barrier to entry.** Free tier + $0.03/run = easy experimentation.
3. **Scales with success.** As agents deliver more value, spend increases naturally.
4. **Transparent.** No hidden fees, no surprise overages (LLM costs are pass-through).
5. **Defensible.** Once agents are in production generating ROI, the per-run cost is trivially justified.

### Risks of Consumption Pricing

1. **Revenue unpredictability.** Quarterly revenue depends on customer usage patterns.
2. **LLM cost exposure.** If LLM costs rise, customer total cost rises (though Lyzr's margin is unaffected).
3. **Race to zero.** If competitors undercut on per-run pricing, margins compress.
4. **Infrastructure cost floor.** Lyzr still pays for compute -- there's a minimum viable price per run.

---

## Implications for Our Pricing Strategy

If we enter the agent governance space, the pricing model matters:

1. **Don't charge per seat for agent management.** The market is moving to consumption. Seat-based pricing for agents feels disconnected from value.
2. **Consider per-run metering.** Track agent invocations, token usage, and compute consumed. Bill accordingly.
3. **Leverage infrastructure advantage.** We own the compute layer. Our cost floor is lower than Lyzr's (they pay cloud providers). A per-run price that includes GPU/compute could be highly competitive.
4. **Bundle infrastructure + governance.** "Run your agents on our infrastructure AND govern them from our control plane -- one bill, one vendor."
