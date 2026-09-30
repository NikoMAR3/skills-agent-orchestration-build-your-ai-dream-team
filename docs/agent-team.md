# Agent team

For Mona's Project Pulse dashboard, I will use a four-agent custom GitHub Copilot team orchestrated through GitHub Copilot CLI in a Codespace. Each agent is defined under the repository's .github/agents folder and specializes in a different part of the workflow.

- Planner — Model: Claude Opus 4.7 (copilot). Responsibility: research the codebase and documentation, identify risks and dependencies, and produce an implementation plan with file ownership and sequencing. Definition: .github/agents/planner.agent.md.
- Orchestrator — Model: Claude Opus 4.7 (copilot). Responsibility: break the plan into phases, delegate tasks to specialists, coordinate sequential versus parallel work, and verify that the full dashboard hangs together. Definition: .github/agents/orchestrator.agent.md.
- Designer — Model: Gemini 3.1 Pro (copilot). Responsibility: shape the dashboard UX, information hierarchy, accessibility, layout, and styling so the Product Pulse experience feels polished and clear. Definition: .github/agents/designer.agent.md.
- Coder — Model: GPT-5.5 (copilot). Responsibility: implement the dashboard code, fix logic issues, and create any required app support files such as .vscode/launch.json for running the Project Pulse frontend. Definition: .github/agents/coder.agent.md.

This team is coordinated in the Codespace with GitHub Copilot CLI so the Orchestrator can delegate work to the Planner, Designer, and Coder while keeping the build process structured and traceable.
