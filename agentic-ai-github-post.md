# 🤖 Building Agentic AI Workflows on AWS — A Practical Guide

> *From autonomous chatbots to multi-agent orchestration — here's everything you need to go from zero to production-ready Agentic AI.*

---

## 🧠 What is Agentic AI?

Agentic AI refers to AI systems that go beyond answering questions — they **reason, plan, act, and delegate** tasks autonomously on behalf of users. Unlike traditional GenAI that produces a single output, agentic systems can:

- Break down complex goals into sub-tasks
- Use tools (APIs, databases, code interpreters) to take real-world actions
- Reflect on their results and course-correct
- Collaborate with other agents in multi-agent pipelines

Think of it as the difference between a calculator and a junior analyst: one gives you a number, the other figures out *which* number you need — and goes and gets it.

---

## 🏗️ Workshop Structure

This repo walks you through **3 core modules** for building production-grade agentic systems on AWS:

### Module 1 — Build an Agentic Chatbot 💬
Create a chatbot that doesn't just respond — it **plans, uses tools, and reflects** to complete multi-step tasks.

- Tool use and function calling with Amazon Bedrock
- Integrating knowledge bases for RAG-powered responses
- Adding guardrails to keep agents on track
- Using the code interpreter for dynamic computation

### Module 2 — Build an Agentic Workflow ⚙️
Not all agents need a chat interface. This module covers **headless agentic workflows** — background automation pipelines that reason and act without human interaction.

- Event-driven agentic triggers via AWS Lambda
- Long-running workflows with state management
- Human-in-the-loop checkpoints for sensitive decisions
- Observability and tracing for agent runs

### Module 3 — 3rd Party Agentic Frameworks 🔧
Leverage popular open-source frameworks on top of Amazon Bedrock:

| Framework | Best For |
|-----------|----------|
| **LangChain** | General-purpose agent orchestration |
| **LlamaIndex** | Knowledge-heavy, RAG-first workflows |
| **crewAI** | Role-based multi-agent collaboration |
| **Strands Agents** | AWS-native, production-ready agents |
| **smolagents** | Lightweight, fast prototyping |

---

## 🔑 Five Pillars of Responsible Agentic AI Adoption

Before deploying agents at scale, your organization needs to think across these dimensions:

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   1. 🏛️  Governance   — Who owns the agent?         │
│   2. 💡  IP & Data    — What can the agent see?     │
│   3. ⚙️  Technology   — What can the agent do?      │
│   4. 👥  Change Mgmt  — How does the team adapt?    │
│   5. 🔒  Security     — How do we keep it safe?     │
│                                                     │
└─────────────────────────────────────────────────────┘
```

Agentic AI introduces **new decision-making paradigms**. Without clear governance and role definitions, organizations risk fragmented adoption, security vulnerabilities, and workforce misalignment.

---

## 🛠️ AWS Services Used

```
Amazon Bedrock          — Foundation models + agent runtime
Amazon Bedrock AgentCore — Production-ready agent hosting
AWS Lambda              — Tool execution & event triggers
Amazon S3               — Knowledge base document storage
Amazon OpenSearch        — Vector search for RAG
Amazon Q Developer      — AI-assisted coding & debugging
AWS IAM + Guardrails    — Security, permissions & safety controls
```

---

## 🚀 Getting Started

### Prerequisites
- AWS Account with Bedrock model access enabled
- Python 3.11+
- AWS CLI configured

### Installation

```bash
# Clone this repository
git clone https://github.com/your-org/agentic-ai-workshop.git
cd agentic-ai-workshop

# Install base dependencies
pip install -r requirements.txt

# For LangChain module
pip install -r requirements_langchain.txt

# For crewAI module
pip install -r requirements_crewai.txt

# For LlamaIndex module
pip install -r requirements_llama_index.txt
```

### Run your first agent

```python
import boto3
from botocore.config import Config

# Initialize Bedrock client
bedrock = boto3.client(
    service_name="bedrock-agent-runtime",
    region_name="us-east-1"
)

# Invoke your agent
response = bedrock.invoke_agent(
    agentId="YOUR_AGENT_ID",
    agentAliasId="YOUR_ALIAS_ID",
    sessionId="my-session-001",
    inputText="Summarize the Q3 sales report and flag any anomalies."
)

# Stream the response
for event in response["completion"]:
    if "chunk" in event:
        print(event["chunk"]["bytes"].decode("utf-8"), end="")
```

---

## 📐 Agent Design Patterns

### 1. ReAct (Reason + Act)
The agent alternates between reasoning about the problem and taking actions, iterating until the task is complete.

```
Thought → Action → Observation → Thought → Action → ...
```

### 2. Multi-Agent Collaboration
Specialized sub-agents work in parallel or sequence, each handling a specific domain (e.g., a *researcher*, a *summarizer*, and a *writer*).

### 3. Human-in-the-Loop
Agents pause at defined checkpoints to request human approval before taking high-stakes actions (e.g., sending an email, executing a financial transaction).

---

## 🔒 Security Best Practices

- **Least-privilege IAM roles** — Agents should only access what they need
- **KMS encryption** — Encrypt all data at rest and in transit  
- **Bedrock Guardrails** — Define topics the agent must never discuss or act on
- **Audit logging** — Every agent action should be traceable via CloudTrail
- **Input/Output validation** — Sanitize all tool inputs and agent outputs

---

## 📊 Who Should Use This?

| Role | What You'll Get |
|------|----------------|
| **ML Engineers** | Hands-on patterns for building and deploying agents |
| **Solutions Architects** | Architecture blueprints for multi-agent systems |
| **Tech Leads** | Framework comparisons and production readiness checklist |
| **Engineering Managers** | Governance and change management strategies |
| **Executive Stakeholders** | ROI framing and responsible adoption roadmap |

---

## 📚 Learn More

- 📖 [AWS Workshop: Building Agentic Workflows](https://catalog.workshops.aws/building-agentic-workflows/en-US)
- 🛒 [AWS Marketplace: Agentic AI Adoption Workshop](https://aws.amazon.com/marketplace)
- 🎓 [Agentic AI Technical Learning Plan – AWS Skill Builder](https://aws.amazon.com/blogs/apn/introducing-the-agentic-ai-technical-learning-plan-in-aws-skill-builder/)
- 📋 [Amazon Bedrock AgentCore Documentation](https://docs.aws.amazon.com/bedrock/)

---

## 🤝 Contributing

We welcome contributions! Please read [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 📄 License

This project is licensed under the **MIT-0 License** — see [LICENSE](./LICENSE) for details.

---

> *"Agentic AI doesn't just answer questions — it takes action. Build responsibly."*

---

⭐ **If this helped you, drop a star!** | 🐛 Found a bug? [Open an issue](../../issues) | 💬 Questions? [Start a discussion](../../discussions)
