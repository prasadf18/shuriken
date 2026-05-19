<div align="center">

<img src="./logo.svg" width="80" height="80" alt="Shuriken"/>

<h1>shuriken</h1>

<p><strong>Build, run, and manage agent platforms.</strong></p>

<p>
  <img src="https://img.shields.io/badge/status-in%20development-e8350e?style=flat-square&labelColor=0e0e0e" alt="status"/>
  &nbsp;
  <img src="https://img.shields.io/badge/python-3.10%2B-ff6a3d?style=flat-square&labelColor=0e0e0e" alt="python"/>
  &nbsp;
  <img src="https://img.shields.io/badge/license-MIT-f5f3ef?style=flat-square&labelColor=0e0e0e" alt="license"/>
  &nbsp;
  <img src="https://img.shields.io/badge/inspired%20by-agno-888888?style=flat-square&labelColor=0e0e0e" alt="inspired by agno"/>
</p>

<p>
  <a href="#introduction">Introduction</a> ·
  <a href="#architecture">Architecture</a> ·
  <a href="#features">Features</a> ·
  <a href="#get-started">Get Started</a> ·
  <a href="#roadmap">Roadmap</a>
</p>

</div>

---

## Introduction

Shuriken is an SDK for building agent platforms.

- **Build** agents using any framework — LangChain, CrewAI, raw API calls, or custom logic.
- **Run** them as production services with tracing, scheduling, and RBAC.
- **Manage** everything from a single control plane.

Shuriken lets you own your entire agent stack. Maintain full control of your data, context, tools, permissions, memory, and human-review loops. Run your platform in your own cloud.

---

## Architecture

```
┌──────────────────────────────────────────────────────────┐
│  INTERFACES   Slack · Discord · REST / SSE · WebSocket   │
├──────────────────────────────────────────────────────────┤
│  RUNTIME      Agent Orchestrator · Human Approval Loop   │
├──────────────────────────────────────────────────────────┤
│  AGENTS       Any Framework · Any SDK · Raw LLM Calls    │
├──────────────────────────────────────────────────────────┤
│  STORAGE      Sessions · Memory · Traces · Knowledge     │
└──────────────────────────────────────────────────────────┘
```

---

## Features

| | Feature | Description |
|---|---|---|
| ⚡ | **Production API** | 50+ endpoints with SSE & WebSocket support for streaming responses |
| 🔒 | **Security & RBAC** | JWT-based role control, multi-tenant isolation, per-tool admin gating |
| 🗓 | **Scheduling** | Cron-based jobs and background runs — zero external infra needed |
| 🔭 | **Observability** | OpenTelemetry tracing, run history, and full audit logs out of the box |
| 🔧 | **100+ Tools** | Pre-built toolkits for APIs, search, code execution, and data sources |
| 🙋 | **Human in the Loop** | Pause runs mid-flight for user confirmation or admin review |
| 🗄 | **Storage** | Bring your own DB — sessions, memory, knowledge, traces are all yours |
| 🚀 | **Deploy Anywhere** | Docker, Railway, AWS, GCP — any container platform works |

---

## What You Can Build

- **Coda** — A code companion that lives in Slack and works alongside your team in real time.
- **Dash** — A self-learning data agent that grounds answers across 6 layers of context.
- **Scout** — Navigates Slack and Google Drive to surface context and answer questions.
- **Auto-Improver** — An agent platform with a self-improvement loop managed by your coding agent.

---

## Get Started

### 1 · Install

```bash
pip install shuriken
```

### 2 · Build your first agent

```python
from shuriken import Agent, tool

@tool
def search(query: str) -> str:
    # your tool logic here
    return f"Results for: {query}"

agent = Agent(
    name="my-agent",
    model="claude-sonnet-4-20250514",
    tools=[search],
)

agent.run("What is the latest news on AI?")
```

### 3 · Serve as a production API

```bash
shuriken serve
```

SSE, WebSocket, RBAC, and tracing are all live from this single command.

### 4 · Deploy to your cloud

```bash
docker build -t shuriken-app .
docker run -p 8000:8000 shuriken-app
```

Works on Railway, Fly.io, AWS ECS, GCP Cloud Run, or any container host.

---

## Key Principles

> **You own your stack.**
> Shuriken never locks you into a hosted service. Your data, your cloud, your agents.

> **Any framework.**
> Wrap LangChain, CrewAI, AutoGen, or raw LLM calls — the runtime is framework-agnostic.

> **One control plane.**
> A single UI and API to manage every agent, session, trace, and permission.

> **Zero infra overhead.**
> Scheduling, tracing, and RBAC are built in. No external queues or workers needed.

---

## Interfaces

| Interface | Description |
|---|---|
| **Slack** | Slash commands, mentions, DMs |
| **Discord** | Bot commands and threads |
| **REST API** | Standard HTTP with JSON |
| **SSE** | Streaming responses |
| **WebSocket** | Real-time bidirectional |
| **A2A** | Agent-to-agent protocol |

---

## Roadmap

- [ ] Core agent runtime + orchestrator
- [ ] REST / SSE / WebSocket API
- [ ] JWT-based RBAC + multi-tenancy
- [ ] Built-in scheduler (cron + background jobs)
- [ ] OpenTelemetry tracing
- [ ] Human approval middleware
- [ ] Slack + Discord interface adapters
- [ ] 100+ tool integrations
- [ ] Web UI control plane
- [ ] MCP server support

---

## Contributing

This is a personal project. PRs and issues are welcome once the core is stable.

---

## Telemetry

Shuriken logs which model providers are used to prioritise updates. Disable at any time:

```bash
export SHURIKEN_TELEMETRY=false
```

---

<div align="center">

<sub>shuriken &nbsp;·&nbsp; personal project &nbsp;·&nbsp; inspired by <a href="https://agno.com">agno</a></sub>

</div>
