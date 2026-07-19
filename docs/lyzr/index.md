# Lyzr.ai Deep-Dive

## Overview

Lyzr.ai is a full-stack enterprise agent infrastructure platform that enables organizations to build, deploy, and govern autonomous AI agents. Founded in 2023, headquartered in Jersey City, NJ, with operations in 7 countries and 150-200 employees.

Their core thesis: **context engineering is the real driver of agent performance, not LLM selection.** The platform is model-agnostic, framework-agnostic, and cloud-agnostic.

---

## Product Suite at a Glance

```mermaid
graph TB
    subgraph appLayer [Application Layer]
        Architect["Architect<br/>Text-to-App"]
        Jazon["Jazon<br/>AI SDR"]
        Skott["Skott<br/>AI Marketer"]
        Amadeo["Amadeo<br/>Banking OS"]
    end

    subgraph builderLayer [Builder Layer]
        Studio["Agent Studio<br/>No-Code/Low-Code"]
        SuperFlow["SuperFlow<br/>DAG Workflows"]
        Manager["Manager Agent<br/>Dynamic Orchestration"]
    end

    subgraph frameworkLayer [Framework Layer]
        ADK["Agent Development Kit<br/>Python SDK"]
        RAI["Responsible AI<br/>Guardrails"]
        KB["Knowledge Patterns<br/>RAG / Graph-RAG / SQL"]
        Memory["Memory & Cognis<br/>Context Management"]
    end

    subgraph infraLayer [Infrastructure Layer]
        CP["Control Plane<br/>Governance & CI/CD"]
        Sim["Simulation Engine<br/>Pre-Production Testing"]
        Registry["Agent Registry<br/>Identity & Discovery"]
    end

    subgraph deployLayer [Deployment Layer]
        Cloud["Lyzr Cloud"]
        VPC["Customer VPC"]
        OnPrem["On-Premise / Air-Gapped"]
    end

    appLayer --> builderLayer
    builderLayer --> frameworkLayer
    frameworkLayer --> infraLayer
    infraLayer --> deployLayer
```

---

## Sections

| Section | What You'll Learn |
|---------|------------------|
| [Company Profile](company-profile.md) | Founding story, leadership, funding, investors, growth trajectory |
| [Product Architecture](product-architecture.md) | Five-layer stack, how components compose, lifecycle |
| [Control Plane](control-plane.md) | The crown jewel -- governance, CI/CD, identity, registry |
| [Agent Studio & Architect](studio-architect.md) | No-code builder and text-to-app generator |
| [Simulation Engine](simulation-engine.md) | Pre-production testing and automated hardening |
| [Responsible AI](responsible-ai.md) | PII, hallucination, toxicity, bias controls |
| [Pre-Built Agents](prebuilt-agents.md) | Amadeo (banking), Jazon (sales), Skott (marketing) |
| [OGI Vision](ogi-vision.md) | Organizational General Intelligence -- the long-term play |
