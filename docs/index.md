# Shuriken — Agent Orchestration SDK

> Build. Run. Own your agents.

Shuriken is an open SDK for building production-grade agent platforms.  
Framework-agnostic, cloud-agnostic, and fully under your control.

---

## ✦ Overview

Shuriken lets you:

- Build AI agents with tools, memory, and instructions
- Orchestrate multi-agent workflows
- Deploy production-ready agent APIs
- Add storage, auth, scheduling, and observability
- Run anywhere — your cloud, your infra

---

## 🚀 Quick Install

pip install shuriken

---

## ⚙️ Minimal Example

from shuriken import Agent, tool

@tool
def search(query: str) -> str:
    """Search the web"""
    return f"Results for: {query}"

agent = Agent(
    name="my-agent",
    model="claude-sonnet-4-20250514",
    tools=[search],
    instructions="You are a helpful assistant.",
)

response = agent.run("What is agent orchestration?")
print(response.content)

---

## 🧠 Core Concepts

### Agents

An Agent wraps:

- LLM model
- Tools
- Memory
- Session state
- Execution lifecycle

---

### Tools

from shuriken import tool

@tool
def get_weather(city: str) -> dict:
    return {"temp": 22, "condition": "sunny"}

Shuriken auto-generates schemas from type hints.

---

### Orchestrator

from shuriken.orchestrator import Orchestrator

orch = Orchestrator(
    agents=[research_agent, writer_agent]
)

result = await orch.run("Write a report on LLMs")

---

## 🏗 Architecture

1. Interfaces — Slack, Discord, REST, SSE, WebSocket, A2A  
2. Runtime — execution engine, orchestrator, scheduling  
3. Agents — core logic, tools, streaming  
4. Storage — sessions, memory, traces, knowledge bases  

---

## 🗄 Storage (Bring Your Own DB)

from shuriken.storage import MemoryStore

memory = MemoryStore("pgvector://localhost:5432")

Supported:
- PostgreSQL
- Redis
- pgvector
- S3 / GCS (planned)

---

## 🔐 Auth & RBAC

from shuriken.auth import RBAC, Role

rbac = RBAC({
    Role.ADMIN: ["*"],
    Role.USER: ["agents:run"],
    Role.VIEWER: ["sessions:read"],
})

---

## 📡 Production API

shuriken serve

Includes:
- REST endpoints
- SSE streaming
- WebSockets
- Auth middleware
- Trace logging

---

## 📊 Observability

from shuriken.utils import configure_telemetry

configure_telemetry(
    exporter="otlp",
    endpoint="http://localhost:4317",
    service_name="shuriken",
)

Tracks:
- Latency
- Tokens
- Tool calls
- Errors
- Full traces

---

## ⏱ Scheduling

from shuriken.runtime import schedule

@schedule(cron="0 9 * * 1-5")
async def daily_digest():
    await agent.run("Summarize news")

---

## 🚢 Deployment

Docker build:
docker build -t shuriken .

Run:
docker run -p 8000:8000 --env-file .env shuriken

Supports:
- AWS ECS
- GCP Cloud Run
- Fly.io
- Railway
- Kubernetes

---

## 🔌 Interfaces

- Slack bots
- Discord bots
- REST APIs
- SSE streams
- Agent-to-agent (A2A)

---

## 🛣 Roadmap

- Core runtime ✔
- Tool registry ✔
- Streaming ✔
- REST + SSE 🚧
- RBAC 🚧
- Scheduler 🚧
- UI control plane 🚧
- MCP tools 🚧

---

## 🤝 Contributing

git clone https://github.com/your-org/shuriken
cd shuriken
pip install -e ".[dev]"
pytest tests/

Rules:
- One feature per PR
- Include tests
- Keep API minimal

---

## 📜 License

MIT License

---

## 🧭 Philosophy

- Simple, not bloated  
- Composable, not monolithic  
- Owned by developers, not platforms
