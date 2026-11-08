# Agent team

I will use a custom GitHub Copilot CLI agent team in a Codespace to plan, design, build, and validate Mona's Project Pulse dashboard.

| Agent | Role | Contribution to the dashboard |
| --- | --- | --- |
| Orchestrator | Coordinates the work and keeps the specialists aligned | Breaks the project into phases, delegates work by file ownership, checks dependencies, and integrates each result before reporting the outcome. |
| Planner | Builds the implementation strategy | Reviews the repo, identifies the workstreams, estimates dependencies and risks, and defines the step-by-step plan for the dashboard build. |
| Designer | Shapes the experience and visual design | Guides layout, accessibility, project-card hierarchy, status treatment, spacing, and the overall polished dashboard look. |
| Coder | Implements the app and validates it | Creates the static dashboard files and any required launch support so the Project Pulse UI can open reliably in VS Code. |

The workflow is intentionally staged: the Planner defines the roadmap, the Designer improves the experience and information flow, and the Coder turns the approved approach into the final HTML, CSS, and JSON. The Orchestrator keeps those specialist tasks coordinated so Mona's team gets a clear, contributor-friendly Project Pulse dashboard.
