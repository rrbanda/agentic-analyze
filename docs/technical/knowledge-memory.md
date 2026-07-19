# Knowledge & Memory Systems

## Overview

Lyzr treats knowledge and memory as **organizational resources**, not agent-specific configurations. Any agent can connect to shared knowledge bases, and the system is designed so that intelligence compounds across the enterprise.

---

## Knowledge Base Types

### 1. Classic Knowledge Base (RAG)

Standard Retrieval-Augmented Generation using vector databases.

- Upload documents (PDF, Word, text, etc.)
- Automatic chunking, embedding, and indexing
- Semantic search for relevant context
- Configurable retrieval parameters

**Use case:** Policy documents, product manuals, FAQ databases.

### 2. Knowledge Graph (Graph-RAG)

Powered by **Neo4j** for relationship-based reasoning.

- Goes beyond keyword matching to understand relationships between entities
- Captures how concepts, people, processes, and data points connect
- Enables multi-hop reasoning ("Who reports to the person who approved this loan?")

**Use case:** Organizational structures, regulatory dependencies, supply chain relationships.

### 3. Semantic Model (Text-to-SQL)

Allows agents to query structured enterprise data using natural language.

- Maps natural language questions to SQL queries
- Connects to enterprise databases
- Returns structured data that agents can reason over

**Use case:** Business intelligence, reporting, data-driven decision making.

### 4. Agentic RAG

Advanced, multi-step knowledge retrieval where the agent actively decides what information to fetch and how to combine it.

- Agent plans its own retrieval strategy
- Multiple retrieval rounds if initial results are insufficient
- Cross-references multiple knowledge sources

**Use case:** Complex research tasks, regulatory analysis, competitive intelligence.

---

## Memory Systems

### Short-Term Memory

Conversation context within a single session. Maintains thread of discussion.

### Long-Term Memory

Persistent memory across sessions. Agent remembers past interactions with a user or about a topic.

### Cognis (Organizational Memory)

Lyzr's proprietary memory system:

- **Memory-as-a-service** with MCP support
- Can be plugged into Cursor, Claude, or custom agents
- Shared across agents -- one agent's learning is available to others
- Captures prompts, outputs, corrections, and lineage
- Foundation for the OGI (Organizational General Intelligence) vision

---

## Global Contexts

Organization-wide instructions shared across all agents:

- Define company-wide policies, tone guidelines, compliance rules
- Apply consistently without configuring each agent individually
- Override or supplement individual agent instructions

---

## How This Compares

| Feature | Lyzr | LangChain/LangGraph | CrewAI |
|---------|------|-------------------|--------|
| Vector RAG | Native (managed) | Via integrations (Chroma, Pinecone, etc.) | Via integrations |
| Graph-RAG | Native (Neo4j) | Via integrations | Not native |
| Text-to-SQL | Native (Semantic Model) | Via tools/chains | Via tools |
| Agentic RAG | Native | Custom implementation | Custom implementation |
| Cross-agent memory | Cognis (managed) | Custom (requires state management) | Shared memory (basic) |
| Global context | Native | Custom implementation | Not native |
| MCP memory support | Native (Cognis) | Via MCP server | Not native |

### The Competitive Edge

Lyzr's knowledge management is **managed, integrated, and cross-agent by default**. Competitors require assembling multiple tools (vector DB + graph DB + SQL connector + custom memory) and managing them independently.

For enterprises that value speed to production over maximum customizability, Lyzr's integrated approach is compelling. For teams that need deep control over every component, open-source alternatives offer more flexibility at the cost of more integration work.
