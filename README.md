# Project Nightingale Launch Center

A multi-agent voice AI system built in ElevenLabs that lets launch stakeholders query real-time product launch information by speaking — routing questions automatically to the right specialist agent.

---

## What This Does

Instead of searching through launch documents, Slack threads, and status decks, stakeholders can call this voice agent and ask questions like:

- *"Are we ready for launch from an engineering perspective?"*
- *"What's our marketing plan for launch week?"*
- *"Give me a 30-second executive summary — are we on track?"*

The system routes each question to the right specialist and responds with grounded, concise answers sourced directly from the knowledge base.

---

## Architecture

**5 nodes · 12 edges · No code**

```
Start
  └── Greeter (routes intent only — no KB, no hallucination)
        ├── Technical Readiness Specialist
        ├── GTM & Marketing Specialist
        └── Executive Briefing Specialist
                    └── End
```

**Routing:**
- 3 forward edges (Greeter → each specialist)
- 3 end edges (each specialist → End)
- 6 cross-routing edges (all specialists ↔ bidirectional)

---

## Specialist Agents

| Agent | Knowledge Base | Scope |
|---|---|---|
| Technical Readiness Specialist | KB_Technical_Readiness.txt + KB_Launch_Plan.txt | Sprint status, QA, bugs, deployment plan, rollback criteria, on-call rotation |
| GTM & Marketing Specialist | KB_GTM_Marketing.txt + KB_Launch_Plan.txt | Campaigns, press timeline, messaging, competitive landscape, sales enablement |
| Executive Briefing Specialist | All 3 KB files | High-level status, risk register, budget, success metrics, post-launch plan |

**Greeter:** Routes intent only. No KB assigned. Never answers questions directly.

---

## Knowledge Base

Three scoped knowledge base files covering a fictional mobile app v3.0 launch (redesigned checkout + Perks loyalty program):

- **KB_Launch_Plan.txt** — Launch overview, feature details, GTM timeline, stakeholder roles, success metrics, risk register, budget summary
- **KB_Technical_Readiness.txt** — Sprint status, architecture, QA results, deployment plan, rollback criteria, team allocation, on-call rotation
- **KB_GTM_Marketing.txt** — Campaign strategy, channel breakdown, messaging playbook, competitive landscape, sales enablement, marketing metrics

---

## Key Design Decisions

**Greeter as dispatcher, not concierge** — No KB assigned to the Greeter. It routes based on intent keywords only. This prevents hallucination and keeps routing clean.

**KB scoping per specialist** — Each specialist only sees documents relevant to its domain. Prevents information leakage and attention dilution.

**Cross-routing on all 6 edges** — Users can switch topics mid-conversation without restarting. Every specialist can hand off to every other specialist.

**Guardrails in every specialist** — Each agent politely redirects out-of-scope questions to the correct specialist rather than attempting to answer.

**Voice-native response design** — Answers lead with the most important fact first. No bullet dumps. Response length matches urgency.

---

## Stack

- **Platform:** ElevenLabs Conversational AI
- **Model:** Flash (low latency, voice-optimized)
- **Architecture pattern:** Multi-agent orchestration with LLM-based intent routing
- **Knowledge base:** Plain text files, domain-scoped per specialist

---

## Files in This Repo

```
├── README.md
├── Build_Steps.md                  # Step-by-step build instructions
├── KB_Launch_Plan.txt              # Launch plan knowledge base
├── KB_Technical_Readiness.txt      # Engineering status knowledge base
└── KB_GTM_Marketing.txt            # Marketing playbook knowledge base
```

---

## Context

Built as part of a hands-on exploration of multi-agent voice AI architecture patterns using ElevenLabs. The same Greeter → domain specialists → KB scoping pattern is reusable across any data-heavy operational context.

**Related projects:**
- [taskflow-product-health-monitor](https://github.com/praveenjatta/taskflow-product-health-monitor) — Same architecture applied to product health querying (user feedback, support tickets, product metrics)
