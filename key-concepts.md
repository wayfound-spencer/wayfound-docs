---
description: >-
  Wayfound is your entry into the world of AI agent supervision. Here are the
  key concepts you need to get the most out of the platform.
---

# Key Concepts

### Agents

Wayfound supports specialized agents powered by the latest large language models. Agents are designed to accomplish specific, clearly defined tasks. They can interact with users through text, images, and video formats. They can communicate with other agents for help with answering specific questions, and they can take action or access information in third-party systems. Agents are end-to-end, meaning that they can both interact with users and perform workflows. You can connect existing agents built on platforms like LangChain or CrewAI.

### Agent Networks

The best agents are specialized to perform a specific task. Agent networks leverage multiple specialized agents that communicate and collaborate to handle complex tasks. Each agent focuses on its specific expertise while working within the broader network.

### AI Supervisor

The AI Supervisor provides centralized oversight of your agent networks, offering agent performance analysis, agent relationship mapping, and network-wide behavior controls. Learn more in the Supervisor [overview.md](supervisor/overview.md "mention") page.

### Performance

The AI Supervisor continuously evaluates agent performance through user satisfaction metrics, knowledge gap analysis, guideline compliance monitoring, and tool utilization success rates. Learn more in the [performance.md](supervisor/performance.md "mention") page.

### Guidelines&#x20;

Guidelines inform how the AI Manager evaluates agent performance. Wayfound offers two levels of guidelines: [guidelines.md](agents/guidelines.md "mention") for individual agents and [global-guidelines.md](supervisor/global-guidelines.md "mention") guidelines that apply across all agents in the organization.

### Sessions

Sessions provide monitoring capabilities through [recordings.md](sessions/recordings.md "mention") of agent-user interactions.

### Evaluation Rubric

For each agent, the AI Supervisor maintains an **evaluation rubric** — a concise grading guide it distills from your guidelines and from the feedback you've given over time. The rubric captures how your organization interprets each guideline in practice, and every session is scored against it. This makes grading more consistent and increasingly tailored to your business. Learn more in [How the Supervisor Learns](supervisor/how-the-supervisor-learns.md).

### Potential Issues

**Potential issues** are recurring behaviors the AI Supervisor notices that aren't yet covered by any of your guidelines. You can promote a potential issue to a new guideline, confirm it as expected behavior, or dismiss it as a false positive. See [Potential Issues](supervisor/potential-issues.md).

### Open Questions

When the AI Supervisor is uncertain how to judge a behavior, it raises an **open question** for your team rather than guessing. Your answer teaches the Supervisor and refines how it evaluates future sessions. See [Open Questions](supervisor/open-questions.md).
