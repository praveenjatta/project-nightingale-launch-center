# 🚀 Project Nightingale Launch Center

A multi-agent voice AI system built with ElevenLabs. Stakeholders call the agent during a product launch and get instant, role-appropriate answers — technical readiness, marketing status, or an executive briefing — routed automatically to the right specialist.

---

## 🧠 Workflow Overview

**5-node multi-agent architecture:**

```
Start
    ↓
Greeter Agent                  → Identifies intent, routes only (no KB, no answers)
    ↓
Technical Readiness Specialist → Sprint status, QA, deployment, rollback plan
GTM & Marketing Specialist     → Campaigns, press, messaging, sales enablement
Executive Briefing Specialist  → High-level status, risks, budget, metrics
    ↓
End
```

🔁 6 cross-routing edges connect all three specialists bidirectionally, so callers can switch topics mid-conversation without restarting.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| ElevenLabs | Conversational voice AI platform |
| Flash Model | Low-latency LLM tuned for voice |
| Knowledge Base (scoped) | Domain-specific grounding per specialist |
| LLM Edge Conditions | Intent-based routing logic |

---

## 📁 Files

| File | Description |
|------|-------------|
| `Build_Steps.md` | Step-by-step build instructions, system prompts, and edge conditions |
| `KB_Launch_Plan.txt` | Launch overview, GTM timeline, stakeholders, risk register, budget |
| `KB_Technical_Readiness.txt` | Sprint status, architecture, QA, deployment, rollback plan |
| `KB_GTM_Marketing.txt` | Campaign strategy, messaging, competitive landscape, sales enablement |
| `README.md` | Project documentation |

---

## 🚀 How to Use

1. Clone or download this repo
2. Open [ElevenLabs Agents](https://elevenlabs.io/app/agents)
3. Create a blank agent and follow `Build_Steps.md` step by step
4. Upload the three KB `.txt` files to their respective specialist nodes
5. Wire the 12 edges (3 forward, 3 end, 6 cross-routing)
6. Test in Preview mode with mic on

---

## 💡 Example Use Case

**Caller asks:** "Are we ready for launch from an engineering perspective?"

**Agent routes to:** Technical Readiness Specialist

**Response:** Sprint status, QA bug counts, deployment rollout schedule, and rollback criteria — sourced directly from the knowledge base, no guessing.

**Caller follows up:** "What's our marketing plan for launch week?"

**Agent cross-routes to:** GTM & Marketing Specialist — no restart needed.

---

## 🔑 Key Design Decisions

- **Greeter as dispatcher, not concierge** — No KB assigned. Routes on intent only, never answers directly.
- **KB scoping per specialist** — Each specialist sees only its relevant documents, preventing information leakage.
- **Cross-routing on all 6 edges** — Full bidirectional handoff between specialists for natural topic switching.
- **Guardrails baked into every prompt** — Specialists redirect out-of-scope questions instead of guessing.
- **Voice-native response design** — Lead with the answer, use real numbers, match response length to urgency.

---

## 👤 Author

**Praveen Kumar Jatta** — Senior Technical Program Manager | AI Automation Consultant

- 🌐 [jattaai.com](https://jattaai.com)
- 💼 [linkedin.com/in/praveenjatta](https://linkedin.com/in/praveenjatta)
- 🐙 [github.com/praveenjatta](https://github.com/praveenjatta)
- 📅 [Book a free discovery call](https://calendly.com/praveenjatta/free-ai-automation-discovery-call)

---

## 📄 License

MIT License — free to use and modify with attribution.
