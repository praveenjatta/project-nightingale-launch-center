🚀 Project Nightingale Launch Center

A multi-agent voice AI system built with ElevenLabs. Stakeholders call the agent during a product launch and get instant, role-appropriate answers — technical readiness, marketing status, or an executive briefing — routed automatically to the right specialist.


🧠 Workflow Overview

5-node multi-agent architecture:

Start
    ↓
Greeter Agent                  → Identifies intent, routes only (no KB, no answers)
    ↓
Technical Readiness Specialist → Sprint status, QA, deployment, rollback plan
GTM & Marketing Specialist     → Campaigns, press, messaging, sales enablement
Executive Briefing Specialist  → High-level status, risks, budget, metrics
    ↓
End

🔁 6 cross-routing edges connect all three specialists bidirectionally, so callers can switch topics mid-conversation without restarting.


🛠️ Tech Stack

ToolPurposeElevenLabsConversational voice AI platformFlash ModelLow-latency LLM tuned for voiceKnowledge Base (scoped)Domain-specific grounding per specialistLLM Edge ConditionsIntent-based routing logic


📁 Files

FileDescriptionBuild_Steps.mdStep-by-step build instructions, system prompts, and edge conditionsKB_Launch_Plan.txtLaunch overview, GTM timeline, stakeholders, risk register, budgetKB_Technical_Readiness.txtSprint status, architecture, QA, deployment, rollback planKB_GTM_Marketing.txtCampaign strategy, messaging, competitive landscape, sales enablementREADME.mdProject documentation


🚀 How to Use


Clone or download this repo
Open ElevenLabs Agents
Create a blank agent and follow Build_Steps.md step by step
Upload the three KB .txt files to their respective specialist nodes
Wire the 12 edges (3 forward, 3 end, 6 cross-routing)
Test in Preview mode with mic on



💡 Example Use Case

Caller asks: "Are we ready for launch from an engineering perspective?"

Agent routes to: Technical Readiness Specialist

Response: Sprint status, QA bug counts, deployment rollout schedule, and rollback criteria — sourced directly from the knowledge base, no guessing.

Caller follows up: "What's our marketing plan for launch week?"

Agent cross-routes to: GTM & Marketing Specialist — no restart needed.


🔑 Key Design Decisions


Greeter as dispatcher, not concierge — No KB assigned. Routes on intent only, never answers directly.
KB scoping per specialist — Each specialist sees only its relevant documents, preventing information leakage.
Cross-routing on all 6 edges — Full bidirectional handoff between specialists for natural topic switching.
Guardrails baked into every prompt — Specialists redirect out-of-scope questions instead of guessing.
Voice-native response design — Lead with the answer, use real numbers, match response length to urgency.



👤 Author

Praveen Kumar Jatta — Senior Technical Program Manager | AI Automation Consultant


🌐 jattaai.com
💼 linkedin.com/in/praveenjatta
🐙 github.com/praveenjatta
📅 Book a free discovery call



📄 License

MIT License — free to use and modify with attribution.
Project contentJattaAI Consulting — Business & GrowthCreated by youJattaAI_LinkedIn_InMail_Templates.md64 linesmdpdfpdfContentDEMO GUIDE_ Product Launch Command Center.docxdocx1782764404898_DEMO GUIDE_ Product Launch Command Center.docxdocx1782764935381_ASSIGNMENT SOLUTION GUIDE - Week 4 PMs_TPMs.docxdocxpdfKB_GTM_Marketing.txt122 linestxtKB_Launch_Plan.txt141 linestxtKB_Technical_Readiness.txt129 linestxtProduct Launch Command Center — Build Steps.md258 linesmdASSIGNMENT - Product Health Monitor.docx46 linesdocx1782764404897_KB_GTM_Marketing.txt122 linestxt1782764404897_KB_Technical_Readiness.txt129 linestxt1782764404898_KB_Launch_Plan.txt141 linestxt1782764404898_Product Launch Command Center — Build Steps.md258 linesmd1782764728941_ASSIGNMENT - Product Health Monitor.docx46 linesdocx1782764728942_KB_Product_Metrics.txt216 linestxt1782764728942_KB_Support_Tickets.txt209 linestxt1782764728943_KB_User_Feedback.txt211 linestxt1782764728943_Product_Health_Monitor___Build_Steps.md289 linesmd1782764935382_Week 4 Assignment Solution.txt1 linetxt1782787670502_README.md103 linesmd(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.nonce='Hu3zYKDvo/1j0zJ0vmxGkg==';d.innerHTML="window.__CF$cv$params={r:'a12a215abea32163',t:'MTc4MjYyMjg1Mg=='};var a=document.createElement('script');a.nonce='Hu3zYKDvo/1j0zJ0vmxGkg==';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();
