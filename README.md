<div align="center">

<!-- LOGO -->
<img src="https://via.placeholder.com/80x80/0e0e0e/e8350e?text=✦" width="80" height="80" alt="Shuriken logo"/>

# shuriken

**Build, run, and manage agent platforms.**

`agent orchestration` &nbsp;·&nbsp; `personal project` &nbsp;·&nbsp; `inspired by agno`

</div>

---

## Introduction

Shuriken is an SDK for building agent platforms.

- **Build** agents using any agent framework — LangChain, CrewAI, raw API calls, or custom logic.
- **Run** them as production services with tracing, scheduling, and RBAC.
- **Manage** everything from a single control plane.

Shuriken lets you own your entire agent stack. Maintain control of your data, context, tools, permissions, memory, and human-review loops. Run your platform in your own cloud.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│  Interfaces   │  Slack · Discord · REST/SSE · WS    │
├───────────────┼─────────────────────────────────────┤
│  Runtime      │  Agent Orchestrator · Human Approval │
├───────────────┼─────────────────────────────────────┤
│  Agents       │  Framework A · Framework B · Custom  │
├───────────────┼─────────────────────────────────────┤
│  Storage      │  Sessions · Memory · Traces · RAG    │
└─────────────────────────────────────────────────────┘
```

---

## Features

| Feature | Description |
|---|---|
| **Production API** | 50+ endpoints with SSE & WebSocket support for streaming agent responses |
| **Security & RBAC** | JWT-based role control, multi-tenant isolation, per-tool admin gating |
| **Scheduling** | Cron-based jobs and background runs — zero external infra needed |
| **Observability** | OpenTelemetry tracing, run history, and full audit logs out of the box |
| **100+ Tools** | Pre-built toolkits for APIs, search, code execution, and data sources |
| **Human in the Loop** | Pause runs mid-flight for user confirmation or admin review |
| **Storage** | Bring your own DB — sessions, memory, knowledge, traces are all yours |
| **Deploy Anywhere** | Docker, Railway, AWS, GCP — any container platform works |

---

## What You Can Build

- **Coda** — A code companion that lives in Slack and works alongside your team in real time.
- **Dash** — A self-learning data agent that grounds answers across 6 layers of context.
- **Scout** — Navigates Slack and Google Drive to surface context and answer questions.
- **Auto-Improver** — An agent platform with a self-improvement loop managed by your coding agent.

---

## Get Started

**1. Install the SDK**

```bash
pip install shuriken
```

**2. Build your first agent**

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

**3. Serve as a production API**

```bash
shuriken serve
```

SSE, WebSocket, RBAC, and tracing are all live from this single command.

**4. Deploy to your cloud**

```bash
docker build -t shuriken-app .
docker run -p 8000:8000 shuriken-app
```

Works on Railway, Fly.io, AWS ECS, GCP Cloud Run, or any container host.

---

## Key Principles

**You own your stack.** Shuriken never locks you into a hosted service. Your data, your cloud, your agents.

**Any framework.** Wrap LangChain, CrewAI, AutoGen, or raw LLM calls — the runtime is framework-agnostic.

**One control plane.** A single UI and API to manage every agent, session, trace, and permission across your platform.

**Zero infra overhead.** Scheduling, tracing, and RBAC are built in. No external queues, workers, or databases to operate unless you want them.

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

## Interfaces

Expose your agents via:

- **Slack** — slash commands, mentions, DMs
- **Discord** — bot commands and threads
- **REST API** — standard HTTP with JSON
- **SSE** — streaming responses
- **WebSocket** — real-time bidirectional
- **A2A** — agent-to-agent protocol

---

## Contributing

This is a personal project. PRs and issues welcome once the core is stable.

---

## Telemetry

Shuriken logs which model providers are used to prioritize updates. Disable with `SHURIKEN_TELEMETRY=false`.

---

<div align="center">

**shuriken** &nbsp;·&nbsp; personal project &nbsp;·&nbsp; inspired by [agno](https://agno.com)

</div>