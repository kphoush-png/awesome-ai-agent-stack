<div align="center">

# 🧩 Awesome AI Agent Stack [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

**A curated map of the tools, frameworks, and infrastructure for building _production_ AI agents — organized by the layers of the stack you actually build in.**

Most "awesome agent" lists are a flat wall of links. This one is a **stack**: start at the top, work down, and you'll know what each layer is for and which tool to reach for.

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: CC0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](LICENSE)
![Last Commit](https://img.shields.io/github/last-commit/kphoush-png/awesome-ai-agent-stack)
![Stars](https://img.shields.io/github/stars/kphoush-png/awesome-ai-agent-stack?style=social)

</div>

---

## 🗺️ The Stack at a Glance

```
┌───────────────────────────────────────────────────────────┐
│  9. UI & Interaction      chat UIs, agent frontends        │
│  8. Deployment & Runtime  serve, scale, sandbox agents     │
│  7. Observability         trace, debug, monitor            │
│  6. Evaluation & Testing  measure quality, catch regress.  │
│  5. Tools & Actions       MCP, function calling, browsers  │
│  4. Memory & State        short/long-term, vector stores   │
│  3. Retrieval (RAG)       ground answers in your data      │
│  2. Orchestration         multi-agent, graphs, workflows   │
│  1. Frameworks            the core agent loop              │
│  0. Models & Serving      the LLMs underneath              │
└───────────────────────────────────────────────────────────┘
```

> **New here?** Jump to the [🚀 Start-Here Learning Path](#-start-here-learning-path) or the [🧭 Framework Decision Guide](#-framework-decision-guide).

## Contents

- [🚀 Start-Here Learning Path](#-start-here-learning-path)
- [🧭 Framework Decision Guide](#-framework-decision-guide)
- [0. Models & Serving](#0-models--serving)
- [1. Agent Frameworks](#1-agent-frameworks)
- [2. Orchestration & Multi-Agent](#2-orchestration--multi-agent)
- [3. Retrieval (RAG)](#3-retrieval-rag)
- [4. Memory & State](#4-memory--state)
- [5. Tools & Actions](#5-tools--actions)
- [6. Evaluation & Testing](#6-evaluation--testing)
- [7. Observability](#7-observability)
- [8. Deployment & Runtime](#8-deployment--runtime)
- [9. UI & Interaction](#9-ui--interaction)
- [🤖 Coding Agents](#-coding-agents)
- [🏗️ Low-Code / Visual Builders](#️-low-code--visual-builders)
- [📚 Learning Resources](#-learning-resources)
- [🤝 Contributing](#-contributing)

---

## 🚀 Start-Here Learning Path

Building your first agent? Do these in order:

1. **Understand the loop.** An agent = LLM + tools + a loop that decides when to call them. Read Anthropic's [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) and OpenAI's [practical guide to building agents](https://platform.openai.com/docs/guides/agents).
2. **Pick one framework** (see the [decision guide](#-framework-decision-guide)) and ship a single-tool agent.
3. **Add a tool via MCP** so your agent can do something real — see [Tools & Actions](#5-tools--actions).
4. **Add retrieval** only when the agent needs your private data — see [Retrieval](#3-retrieval-rag).
5. **Add evals before you add features** — see [Evaluation](#6-evaluation--testing). This is the step most people skip and later regret.
6. **Add tracing** so you can see what the agent actually did — see [Observability](#7-observability).

> 💡 **The #1 mistake:** reaching for multi-agent orchestration on day one. Start with one good agent and a tight eval loop.

---

## 🧭 Framework Decision Guide

| If you want… | Reach for | Why |
| --- | --- | --- |
| Minimal, model-native, few dependencies | **OpenAI Agents SDK**, **Pydantic AI** | Thin layer over the model; easy to reason about |
| Explicit control over state & branching | **LangGraph** | Graph/state-machine model; great for complex flows |
| Role-based teams of agents, fast to prototype | **CrewAI**, **AutoGen** | High-level "crew"/conversation abstractions |
| Batteries-included, one SDK for everything | **LlamaIndex**, **Agno**, **Haystack** | Data + agents + tools in one place |
| Enterprise / .NET & C# shops | **Semantic Kernel** | First-class Microsoft ecosystem support |
| Prompt/pipeline optimization as code | **DSPy** | Programmatic prompts, compiled & optimized |

> No single "best" framework — pick the smallest one that fits your control needs, then grow.

---

## 0. Models & Serving

> **What this layer is for:** the LLMs your agent reasons with, and how you run them.

- [Ollama](https://github.com/ollama/ollama) — Run open models (Llama, Qwen, Mistral…) locally with one command.
- [vLLM](https://github.com/vllm-project/vllm) — High-throughput, memory-efficient inference server for production.
- [SGLang](https://github.com/sgl-project/sglang) — Fast serving framework for LLMs and vision models; strong structured-output support.
- [Text Generation Inference (TGI)](https://github.com/huggingface/text-generation-inference) — Hugging Face's production inference server for open models.
- [LiteLLM](https://github.com/BerriAI/litellm) — One OpenAI-compatible API in front of 100+ model providers; essential for provider-agnostic agents.
- [llama.cpp](https://github.com/ggml-org/llama.cpp) — Fast CPU/GPU inference for GGUF models; powers much of the local ecosystem.
- [LM Studio](https://lmstudio.ai/) — Desktop app for running and serving local models with a GUI.

## 1. Agent Frameworks

> **What this layer is for:** the core agent loop — give an LLM tools and let it decide what to do.

- [LangChain](https://github.com/langchain-ai/langchain) — The most widely adopted framework; huge integration surface.
- [LangGraph](https://github.com/langchain-ai/langgraph) — Low-level, graph-based orchestration for stateful, controllable agents.
- [LlamaIndex](https://github.com/run-llama/llama_index) — Data-framework-turned-agent-framework; strong on RAG + agents.
- [OpenAI Agents SDK](https://github.com/openai/openai-agents-python) — Lightweight, model-native agents with handoffs and guardrails.
- [Pydantic AI](https://github.com/pydantic/pydantic-ai) — Type-safe agents built on Pydantic; clean and minimal.
- [CrewAI](https://github.com/crewAIInc/crewAI) — Role-playing autonomous agents that collaborate as a "crew."
- [Microsoft AutoGen](https://github.com/microsoft/autogen) — Multi-agent conversation framework from Microsoft Research.
- [Microsoft Agent Framework](https://github.com/microsoft/agent-framework) — Microsoft's unified successor to AutoGen + Semantic Kernel.
- [Semantic Kernel](https://github.com/microsoft/semantic-kernel) — Microsoft's SDK for AI orchestration across .NET, Python, Java.
- [Agno](https://github.com/agno-agi/agno) — Full-stack framework for multi-modal agents (formerly Phidata).
- [Mastra](https://github.com/mastra-ai/mastra) — TypeScript framework bundling agents, workflows, memory, evals, and observability.
- [Strands Agents](https://github.com/strands-agents/sdk-python) — AWS's model-driven, lightweight agent SDK.
- [DSPy](https://github.com/stanfordnlp/dspy) — Programmatic prompting: define pipelines in code and let them be compiled/optimized.
- [Haystack](https://github.com/deepset-ai/haystack) — Composable pipelines for RAG and agents.
- [Atomic Agents](https://github.com/BrainBlend-AI/atomic-agents) — Minimal, modular, "Lego-block" approach to agents.
- [smolagents](https://github.com/huggingface/smolagents) — Tiny agent library from Hugging Face; agents that write code as actions.

## 2. Orchestration & Multi-Agent

> **What this layer is for:** coordinating several agents, long-running workflows, and durable execution.

- [MetaGPT](https://github.com/FoundationAgents/MetaGPT) — Multi-agent framework that simulates a software company.
- [CAMEL](https://github.com/camel-ai/camel) — Research framework for communicative multi-agent systems.
- [Temporal](https://github.com/temporalio/temporal) — Durable execution engine; increasingly used to make agent workflows reliable.
- [Burr](https://github.com/apache/burr) — State machines for decision-making applications and agents.
- [Agent Development Kit (ADK)](https://github.com/google/adk-python) — Google's framework for building and orchestrating agents.
- [mcp-agent](https://github.com/lastmile-ai/mcp-agent) — Build agents that compose and orchestrate across multiple MCP servers.
- [A2A (Agent2Agent)](https://github.com/a2aproject/A2A) — Open protocol for interoperability between independent agents.

## 3. Retrieval (RAG)

> **What this layer is for:** grounding agents in your own documents and data. **Vector databases:**

- [Qdrant](https://github.com/qdrant/qdrant) — High-performance vector search engine in Rust.
- [Weaviate](https://github.com/weaviate/weaviate) — Open-source vector database with hybrid search.
- [Chroma](https://github.com/chroma-core/chroma) — Developer-friendly embedded vector store; great for prototyping.
- [Milvus](https://github.com/milvus-io/milvus) — Cloud-native vector DB built for scale.
- [pgvector](https://github.com/pgvector/pgvector) — Vector similarity search inside PostgreSQL.

**Retrieval tooling:**

- [RAGFlow](https://github.com/infiniflow/ragflow) — RAG engine with deep document understanding.
- [txtai](https://github.com/neuml/txtai) — All-in-one embeddings database for semantic search and RAG.

## 4. Memory & State

> **What this layer is for:** giving agents short- and long-term memory beyond the context window.

- [Mem0](https://github.com/mem0ai/mem0) — A memory layer for AI agents and assistants.
- [Letta](https://github.com/letta-ai/letta) — Stateful agents with long-term memory (formerly MemGPT).
- [Zep](https://github.com/getzep/zep) — Long-term memory and context engineering for agents.
- [Graphiti](https://github.com/getzep/graphiti) — Build real-time, temporally-aware knowledge graphs for agent memory.
- [Cognee](https://github.com/topoteretes/cognee) — Memory for agents using knowledge graphs + vector stores.

## 5. Tools & Actions

> **What this layer is for:** letting agents *do* things — call APIs, browse, run code. The **Model Context Protocol (MCP)** is becoming the standard interface here.

- [Model Context Protocol](https://github.com/modelcontextprotocol) — Open standard for connecting agents to tools and data (spec + SDKs).
- [FastMCP](https://github.com/jlowin/fastmcp) — The fast, Pythonic way to build MCP servers and clients ("FastAPI for MCP").
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers) — Directory of ready-to-use MCP servers.
- [Composio](https://github.com/ComposioHQ/composio) — 250+ ready-made tool integrations for agents.
- [Browser Use](https://github.com/browser-use/browser-use) — Let agents control a real browser.
- [E2B](https://github.com/e2b-dev/E2B) — Secure cloud sandboxes for running agent-generated code.
- [Stagehand](https://github.com/browserbase/stagehand) — AI browser automation framework.

## 6. Evaluation & Testing

> **What this layer is for:** measuring whether your agent is actually good, and catching regressions. **Do this early.**

- [Ragas](https://github.com/explodinggradients/ragas) — Evaluation toolkit for RAG and agent pipelines.
- [DeepEval](https://github.com/confident-ai/deepeval) — "Pytest for LLMs" — unit-test your agents.
- [promptfoo](https://github.com/promptfoo/promptfoo) — Test, evaluate, and red-team prompts and agents from the CLI.
- [Opik](https://github.com/comet-ml/opik) — Open-source eval + tracing platform (Apache-2.0) from Comet.
- [Inspect AI](https://github.com/UKGovernmentBEIS/inspect_ai) — Rigorous evals framework from the UK AI Safety Institute.
- [Phoenix](https://github.com/Arize-ai/phoenix) — Open-source eval + observability from Arize.

## 7. Observability

> **What this layer is for:** seeing what your agent actually did — every call, token, and tool use.

- [Langfuse](https://github.com/langfuse/langfuse) — Open-source LLM engineering platform: tracing, evals, prompt management.
- [Helicone](https://github.com/Helicone/helicone) — Observability and logging proxy for LLM apps.
- [Laminar](https://github.com/lmnr-ai/lmnr) — Open-source tracing + evals platform built for agent engineering (Apache-2.0).
- [AgentOps](https://github.com/AgentOps-AI/agentops) — Session replay, metrics, and monitoring for agents (fully open-source dashboard).
- [OpenLLMetry](https://github.com/traceloop/openllmetry) — OpenTelemetry-based observability for LLM apps.

## 8. Deployment & Runtime

> **What this layer is for:** serving agents as APIs, scaling them, and sandboxing their actions.

- [LangServe](https://github.com/langchain-ai/langserve) — Deploy LangChain runnables as REST APIs.
- [BentoML](https://github.com/bentoml/BentoML) — Build and ship AI apps and model-serving endpoints.
- [Modal](https://modal.com/) — Serverless cloud for running Python/AI workloads without infra.

## 9. UI & Interaction

> **What this layer is for:** the frontend your users actually touch.

- [Open WebUI](https://github.com/open-webui/open-webui) — Feature-rich, self-hosted chat UI for local and remote models.
- [Chainlit](https://github.com/Chainlit/chainlit) — Build conversational agent UIs in pure Python.
- [AG-UI / CopilotKit](https://github.com/CopilotKit/CopilotKit) — React toolkit for embedding agents into apps.
- [assistant-ui](https://github.com/assistant-ui/assistant-ui) — React components for AI chat.

## 🤖 Coding Agents

> Agents that write, edit, and debug code — the most commercially proven agent category.

- [OpenHands](https://github.com/All-Hands-AI/OpenHands) — Autonomous software-engineering agents (formerly OpenDevin).
- [Aider](https://github.com/Aider-AI/aider) — AI pair programming in your terminal.
- [Cline](https://github.com/cline/cline) — Autonomous coding agent in your IDE.
- [SWE-agent](https://github.com/SWE-agent/SWE-agent) — Agents that fix GitHub issues autonomously (Princeton).
- [Continue](https://github.com/continuedev/continue) — Open-source AI code assistant for VS Code and JetBrains.
- [OpenCode](https://github.com/sst/opencode) — Open-source AI coding agent built for the terminal.
- [Roo Code](https://github.com/RooCodeInc/Roo-Code) — Autonomous coding agent (a VS Code fork of the Cline lineage) with multiple modes.
- [Goose](https://github.com/block/goose) — Local, extensible on-machine coding/automation agent from Block.
- [Codex CLI](https://github.com/openai/codex) — OpenAI's lightweight coding agent for the terminal.

## 🏗️ Low-Code / Visual Builders

> Build agents and workflows without (much) code.

- [Dify](https://github.com/langgenius/dify) — Open-source platform for building LLM apps and agents visually.
- [n8n](https://github.com/n8n-io/n8n) — Workflow automation with growing AI/agent nodes.
- [Flowise](https://github.com/FlowiseAI/Flowise) — Drag-and-drop builder for LLM flows and agents.
- [Langflow](https://github.com/langflow-ai/langflow) — Visual framework for building multi-agent and RAG apps.

## 📚 Learning Resources

- [Anthropic — Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) — The best short read on agent design patterns.
- [OpenAI — A Practical Guide to Building Agents](https://platform.openai.com/docs/guides/agents) — Vendor-neutral enough to be broadly useful.
- [Hugging Face — Agents Course](https://huggingface.co/learn/agents-course) — Free, hands-on course.
- [DeepLearning.AI — short courses on agents](https://www.deeplearning.ai/short-courses/) — Bite-sized, framework-specific.

---

## 🤝 Contributing

Contributions make this list better for everyone. Please read [CONTRIBUTING.md](CONTRIBUTING.md) first.

**The bar:** entries must be open-source (or have a meaningful free/open tier), actively maintained, and genuinely useful — not just popular. One line, present tense, says *what it does* and *why it belongs in that layer*.

Open an [issue](../../issues/new/choose) to suggest a tool, or send a PR.

---

<div align="center">

**Found this useful? [⭐ Star the repo](../../stargazers) — it helps others find it.**

Maintained by the community. Licensed [CC0](LICENSE) — do whatever you want with it.

</div>
