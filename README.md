# Moordock

**Your AI. Your Infrastructure. Your Rules.**

Moordock is an on-premise LLM orchestration platform that anchors large language models inside your own infrastructure. No cloud dependency. No data leakage. Full enterprise-grade control — built specifically for Microsoft Dynamics 365 and AX environments.

---

## Why Moordock?

Cloud-based AI creates unacceptable risk for enterprises running mission-critical ERP. Financial records, supply chain data, and business logic should not flow through third-party servers.

Moordock solves this by running AI inference entirely on your hardware, with native connectors to D365 and AX so your teams get the productivity gains without surrendering data sovereignty.

---

## Features

| Feature | Description |
|---|---|
| **Local inference** | Runs Llama, Mistral, Qwen, DeepSeek on your own hardware via Ollama or llama.cpp |
| **D365 / AX native** | MCP server connector built in C# for Dynamics 365 and AX |
| **Model agnostic** | Swap models without changing your integration layer |
| **Air-gap ready** | Designed for HIPAA, GDPR, and SOC 2 environments |
| **Agentic pipelines** | Multi-step AI agents fully contained within your infrastructure |

---

## Quick Start

### Prerequisites

- Windows Server 2019+ or Ubuntu 22.04+
- 16GB RAM minimum (32GB recommended for 8B+ models)
- [Ollama](https://ollama.com) installed
- .NET 8 SDK

### Install

```bash
git clone https://github.com/jhodge6570/moordock.git
cd moordock
ollama pull llama3
moordock init --model llama3 --port 11434
```

### Connect to D365

```bash
moordock connect d365 --url https://your-org.crm.dynamics.com --client-id YOUR_APP_ID --tenant-id YOUR_TENANT_ID
moordock status
# Model: Llama 3 8B · Endpoint: localhost:11434 · D365: connected · Cloud: none
```

### Query your ERP

```bash
moordock query "Show me all purchase orders over $10,000 that are past due"
moordock query "Summarize inventory variance for warehouse A this quarter"
moordock query "Which vendors have outstanding invoices older than 90 days?"
```

---

## D365 MCP Server (C#)

```csharp
services.AddMoordock(options =>
{
    options.ModelEndpoint = "http://localhost:11434";
    options.Model = "llama3";
    options.AllowedEntities = new[] { "SalesOrder", "PurchaseOrder", "InventTable" };
    options.MaxTokens = 2048;
});
```

---

## Use Cases

1. **AI-Augmented ERP Queries** - Natural language against live D365 data, no cloud exposure
2. **Private Document Intelligence** - Query contracts and SOPs on-premise
3. **Legacy AX Modernization** - Retrofit AI into AX 2009/2012 without cloud migration
4. **Agentic Automation** - Multi-step AI pipelines, fully contained

---

## Roadmap

- [x] Local LLM runtime (Ollama integration)
- [x] D365 MCP server connector (C#)
- [ ] AX 2009 / AX 2012 connector
- [ ] Web UI for non-technical users
- [ ] PII scrubbing layer
- [ ] Multi-model routing
- [ ] Fine-tuning pipeline

---

## Tech Stack

- **Runtime**: Ollama / llama.cpp
- **Connector**: C# / .NET 8
- **ERP**: Microsoft Dynamics 365, AX 2009/2012
- **Protocol**: Model Context Protocol (MCP)
- **Languages**: C#, X++, Python (tooling)

---

## Contact

hello@moordock.com | moordock.com

---

*Built by a 40-year enterprise IT veteran who got tired of watching financial data flow through other people's servers.*
