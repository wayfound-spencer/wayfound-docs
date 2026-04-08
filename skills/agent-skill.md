# Agent Skill

Wayfound publishes an open-source [https://agentskills.io](https://agentskills.io/) that teaches AI coding agents how to integrate Wayfound into your application. When a developer asks their coding agent to "add Wayfound  supervision" or "send session transcripts to Wayfound," the agent automatically knows how to wire up the SDK and API.&#x20;

#### What is an Agent Skill?

An agent skill is a portable set of instructions that gives AI coding agents new capabilities. Skills follow the [https://agentskills.io](https://agentskills.io/) open standard and are supported by leading AI development tools including Claude Code, Codex, Cursor, Gemini CLI, and many others.

&#x20;                                                                                                                                                                                                   The Wayfound skill teaches your coding agent:                                                                                                                                                                                              &#x20;

&#x20; \- How to install and configure the Wayfound Python and JavaScript SDKs                                                                                                                            &#x20;

&#x20; \- How to format session messages using all 14 supported event types

&#x20; \- How to send completed or streaming session transcripts to Wayfound via SDK or REST API                                                                                                          &#x20;

&#x20; \- How to set up visitor tracking, account tracking, and session metadata&#x20;

### Install

#### Claude Code

This is available as a Claude Code plugin marketplace. To install:                                                                                                                                &#x20;

&#x20; 1\. Add the marketplace:                                                                                                                                                                           &#x20;

&#x20; `/plugin marketplace add Wayfound-AI/wayfound-agent-skills`

&#x20; 2\. Open `/plugin`, go to the Marketplaces tab, select wayfound-skills, browse plugins, and install wayfound&#x20;

#### Other Agents

Any agent that supports the [https://agentskills.io](https://agentskills.io/) format can use this skill. Check your agent's documentation for how it discovers and loads skills.

#### Source

The skill is open source and available on GitHub: [https://github.com/Wayfound-AI/wayfound-agent-skills](https://github.com/Wayfound-AI/wayfound-agent-skills)
