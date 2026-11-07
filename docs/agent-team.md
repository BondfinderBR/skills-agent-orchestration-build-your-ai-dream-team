# Agent team

I will use GitHub Copilot CLI in a Codespace to orchestrate this team to plan, design, build, and validate Mona's Project Pulse dashboard.

| Agent | Model | Responsibility | Definition |
| --- | --- | --- | --- |
| Orchestrator | Claude Opus 5.5 | Coordinates the specialists, phases their work by file ownership and dependencies, integrates their results, and reports the outcome. | `.github/agents/orchestrator.agent.md` |
| Planner | Claude Opus 5.5 | Researches the repository and produces an implementation plan with steps, ownership, dependencies, risks, and validation expectations. | `.github/agents/planner.agent.md` |
| Designer | Gemini 3.7 Flash | Guides the dashboard's usability, accessibility, information hierarchy, responsive layout, and visual design. | `.github/agents/designer.agent.md` |
| Coder | GPT-5.5 | Implements the assigned dashboard files and runnable-app support, then validates the implementation. | `.github/agents/coder.agent.md` |

The Orchestrator will involve the Planner before implementation, then coordinate the Designer and Coder so design and coding work fit together. The dashboard will present project names, owners, status, recent activity, priority, and contributor-friendly summaries.
