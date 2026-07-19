# Architecture Patterns

## Orchestration Patterns in Production

Lyzr supports five orchestration patterns that dominate enterprise deployments in 2026. Most production systems combine multiple patterns.

---

## Pattern 1: Sequential (Chain)

Agents execute in order. Each agent's output feeds the next agent's input.

```mermaid
graph LR
    A["Agent A<br/>Research"] --> B["Agent B<br/>Analyze"] --> C["Agent C<br/>Write"] --> D["Agent D<br/>Review"]
```

**Best for:** Linear workflows with clear handoffs (e.g., research → draft → review → publish).

---

## Pattern 2: Parallel (Fan-Out / Fan-In)

Multiple agents execute simultaneously. Results are merged.

```mermaid
graph TB
    Input["Input"] --> A["Agent A<br/>Market Research"]
    Input --> B["Agent B<br/>Competitor Analysis"]
    Input --> C["Agent C<br/>Customer Feedback"]
    A --> Merge["Merge Results"]
    B --> Merge
    C --> Merge
    Merge --> Output["Synthesized Report"]
```

**Best for:** Independent subtasks that can run concurrently (e.g., multi-source research).

---

## Pattern 3: Hierarchical (Manager + Workers)

A manager agent decomposes goals and delegates to specialist workers.

```mermaid
graph TB
    Manager["Manager Agent<br/>Decomposes & Delegates"]
    Manager --> W1["Worker: Document Verification"]
    Manager --> W2["Worker: Credit Check"]
    Manager --> W3["Worker: Compliance Screening"]
    W1 --> Manager
    W2 --> Manager
    W3 --> Manager
    Manager --> Output["Synthesized Decision"]
```

**Best for:** Complex, goal-driven tasks where the execution path varies by input (e.g., KYC processing).

---

## Pattern 4: Handoff (Routing)

Route the user to the right team or agent based on intent.

```mermaid
graph TB
    Router["Router Agent<br/>Intent Classification"]
    Router -->|"billing"| Billing["Billing Agent"]
    Router -->|"technical"| Tech["Technical Support Agent"]
    Router -->|"sales"| Sales["Sales Agent"]
    Router -->|"escalation"| Human["Human Agent"]
```

**Best for:** Customer-facing systems with multiple specialized teams.

---

## Pattern 5: Loop (Iteration with Evaluation)

Repeat until quality threshold is met.

```mermaid
graph TB
    Generate["Generate Draft"]
    Evaluate["Evaluate Quality"]
    Generate --> Evaluate
    Evaluate -->|"below threshold"| Generate
    Evaluate -->|"above threshold"| Output["Final Output"]
```

**Best for:** Quality-sensitive content generation, code review cycles.

---

## Hybrid Pattern (Production Standard)

Most enterprise deployments combine patterns:

1. **Handoff** at the top → route to the right team
2. **Hierarchical** within each team → manager delegates to specialists
3. **Sequential or parallel** within each specialist's workflow
4. **Loop** for quality-sensitive steps

---

## Vertical Reference Architectures

### Banking: KYC Processing (Amadeo)

```mermaid
graph TB
    Customer["Customer Application"]
    Manager["Manager Agent"]
    DocVerify["Document Verification<br/>Agent"]
    CreditCheck["Credit Bureau<br/>Agent"]
    Sanctions["Sanctions Screening<br/>Agent"]
    RiskScore["Risk Assessment<br/>Agent"]
    Compliance["Compliance Check<br/>Agent"]
    AccountProv["Account Provisioning<br/>Agent"]
    HIL["Human Review<br/>(Edge Cases Only)"]

    Customer --> Manager
    Manager --> DocVerify
    Manager --> CreditCheck
    Manager --> Sanctions
    DocVerify --> RiskScore
    CreditCheck --> RiskScore
    Sanctions --> RiskScore
    RiskScore -->|"clear"| Compliance --> AccountProv
    RiskScore -->|"flagged"| HIL --> Compliance
```

**Results:** 5x faster onboarding, 60% compliance workload reduction, ~$1.02/run.

### Sales: SDR Workflow (Jazon)

```mermaid
graph TB
    Pipeline["CRM Pipeline Data"]
    Objective["Revenue Objective"]
    Intelligence["Intelligence Layer<br/>Account + Intent + Context"]
    Registry["Agent Registry<br/>400+ Agents"]

    Pipeline --> Intelligence
    Objective --> Intelligence
    Intelligence --> Registry

    Registry --> Prospecting["Prospecting Agents"]
    Registry --> Enrichment["Enrichment Agents"]
    Registry --> Outreach["Outreach Agents"]
    Registry --> Nurture["Deal Nurturing Agents"]
    Registry --> Proposal["Proposal Agents"]

    Prospecting --> Meetings["Meetings Booked"]
    Enrichment --> Meetings
    Outreach --> Meetings
    Nurture --> Deals["Deals Progressed"]
    Proposal --> Deals
```

### Telecom: Operations Monitoring

Parallel orchestration for telemetry processing across distributed assets:

- Multiple agents simultaneously analyze sensor data, weather feeds, and ticketing system events
- Aggregate into unified operational dashboard
- Flags exceptions for human review

### Government: Air-Gapped Deployment

Cross-framework orchestration in air-gapped environments:

- Agents from multiple frameworks operating under one identity, observability, and policy enforcement model
- Infrastructure never touches the public internet
- CISO-approvable and auditable

---

## SuperFlow Node Types (Production DAG Builder)

| Category | Nodes | Purpose |
|----------|-------|---------|
| **AI Nodes** | AI Agent, A2A Agent, LLM, AI Swarm, Tool | Execute intelligence |
| **Logic Nodes** | If, Switch, Loop, Filter, Merge, Stop/Error, Wait, NoOp | Control flow |
| **Integration** | HTTP Request, Code Block, Webhook Trigger | External systems |
| **Governance** | Wait for Approval | Human-in-the-loop |
| **Scheduling** | Cron Trigger | Recurring execution |
