# SDK & Developer Experience

## Lyzr ADK (Agent Development Kit)

| Attribute | Detail |
|-----------|--------|
| Package | `lyzr-adk` |
| Version | v0.1.11 (June 2026) |
| License | MIT |
| Python | >= 3.8 |
| PyPI | [pypi.org/project/lyzr-adk](https://pypi.org/project/lyzr-adk/) |
| GitHub | [github.com/pradipta-lyzr/lyzr-sdk](https://github.com/pradipta-lyzr/lyzr-sdk) |
| Docs | [docs.lyzr.ai](https://docs.lyzr.ai) |
| Discord | [discord.gg/lyzr](https://discord.gg/lyzr) |

---

## Quick Start

```python
from lyzr import Studio

# Initialize the SDK
studio = Studio(api_key="your-api-key")

# Create an agent
agent = studio.create_agent(
    name="Assistant",
    provider="gpt-4o",
    role="Helpful assistant",
    goal="Help users with their questions",
    instructions="Be concise and accurate"
)

# Run the agent
response = agent.run("What is machine learning?")
print(response.response)
```

---

## API Surface

### Core Classes

| Class | Purpose |
|-------|---------|
| `Studio` | Main entry point. Manages auth, connections, all resource CRUD. |
| `Agent` | AI-powered entity with provider, role, goal, instructions |
| `KnowledgeBase` | RAG-powered document retrieval |
| `Memory` | Conversation context across sessions |
| `Context` | Background information as key-value pairs |
| `RAIPolicy` | Responsible AI configuration (toxicity, PII, injection) |

### Studio Methods

```python
# Agent lifecycle
studio.create_agent(name, provider, role, goal, instructions, temperature, ...)
studio.get_agent(agent_id)
studio.list_agents()

# Knowledge bases
studio.create_knowledge_base(name, description)
kb.upload_document(file_path)

# Contexts
studio.create_context(name, content)

# RAI Policies
studio.create_rai_policy(name, config)

# Memory
studio.create_memory_credential(config)
```

### Agent Configuration Options

| Parameter | Type | Description |
|-----------|------|-------------|
| `name` | str | Agent name |
| `provider` | str | LLM model (e.g., "gpt-4o", "claude-sonnet-4") |
| `role` | str | Agent's role description |
| `goal` | str | What the agent aims to achieve |
| `instructions` | str | Behavioral instructions |
| `temperature` | float | Creativity (0.0 - 2.0) |
| `top_p` | float | Nucleus sampling (0.0 - 1.0) |
| `response_model` | BaseModel | Pydantic model for structured output |
| `memory` | Memory | Memory configuration |
| `contexts` | list | Background context objects |
| `rai_policy` | RAIPolicy | Responsible AI policy |
| `file_generation` | bool | Enable file output |
| `image_config` | ImageModelConfig | Image generation settings |

### Supported Providers

| Provider | Models |
|----------|--------|
| OpenAI | GPT-4o, GPT-4o-mini, GPT-5, o3, o4-mini |
| Anthropic | Claude Sonnet 4/4.5, Claude Opus 4/4.5 |
| Google | Gemini 2.x, Gemini 3.0 Pro |
| Amazon Bedrock | Various models via Bedrock |
| Groq | Fast inference models |
| Perplexity | Search-augmented models |

---

## Developer Experience Assessment

### Strengths

1. **Simple API.** `Studio` → `create_agent` → `agent.run()` is a 3-line path to a working agent. Lower cognitive load than LangGraph's StateGraph model.
2. **Managed infrastructure.** No need to set up vector databases, memory stores, or serving infrastructure. Everything is handled by the platform.
3. **RAI built-in.** Attaching responsible AI guardrails is a configuration, not a code change.
4. **Studio ↔ ADK parity.** Agents built in Studio are accessible via ADK and vice versa. No separate codebases.
5. **Structured output.** Native Pydantic model support for typed responses.

### Weaknesses

1. **Beta maturity.** v0.1.11 -- still pre-1.0. API surface may change. Limited battle-testing compared to LangGraph (47M+ monthly downloads).
2. **Platform dependency.** Requires Lyzr API key and Lyzr infrastructure. No pure offline/self-hosted SDK mode.
3. **Limited documentation depth.** Docs are functional but lack the depth and community examples of LangChain/LangGraph.
4. **GitHub activity.** The open-source framework repo ([LyzrCore/lyzr-framework](https://github.com/LyzrCore/lyzr-framework)) has limited stars and contributors compared to competitors.
5. **Python-only.** No TypeScript, Go, or Java SDK (though REST API is language-agnostic).

---

## Comparison with Competitors

| Dimension | Lyzr ADK | LangGraph | CrewAI |
|-----------|---------|-----------|--------|
| **Abstraction Level** | High (managed platform) | Low (graph primitives) | Medium (role-based crews) |
| **Learning Curve** | Low (3-line quick start) | High (StateGraph, nodes, edges) | Medium (agents, tasks, processes) |
| **Production Readiness** | Enterprise features built-in | Production-proven at scale | Growing production adoption |
| **Customizability** | Moderate (configuration-driven) | Very high (code everything) | High (code + config) |
| **State Management** | Managed (memory, contexts) | Native (checkpoints, persistence) | Basic (shared memory) |
| **Testing** | Simulation Engine (native) | LangSmith (separate tool) | Manual testing |
| **Governance** | Control Plane (native) | None built-in | None built-in |
| **Community** | Small but growing | Very large (47M+ PyPI/mo) | Large (51K stars) |
| **Vendor Lock-in** | High (Lyzr platform) | Low (MIT, self-hosted) | Low (MIT, self-hosted) |

### The Trade-off

Lyzr offers **higher abstraction + enterprise features** at the cost of **vendor lock-in + less customizability**. LangGraph offers **maximum control + no lock-in** at the cost of **more code + no built-in governance**. The right choice depends on whether the customer values speed-to-production or maximum flexibility.

---

## Lyzr Blocks (Modular Components)

For organizations not ready to adopt the full platform, Lyzr offers standalone modules:

| Block | Function | Use From |
|-------|----------|----------|
| **Knowledge Base** | RAG-as-a-service endpoint | LangChain, Semantic Kernel, any framework |
| **Cognis** | Memory-as-a-service with MCP support | Cursor, Claude, custom agents |
| **Responsible AI** | Guardrails-as-a-service | Any pipeline |

This is a smart land-and-expand strategy: start with one module, demonstrate value, expand to the full platform.
