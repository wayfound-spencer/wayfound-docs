---
description: >-
  Actions allow you to create interactions between agents, give your agents
  access to tools, and connect them to 3rd party integrations.
hidden: true
---

# Actions

{% hint style="warning" %}
Actions are only available for agents built on Wayfound
{% endhint %}

AI agents are often promoted as general purpose solutions, but they work most reliably and effectively when deployed for a particular purpose. The set of diverse and complex problems faced by any business can be best solved using a **Multi-Agent System**, or a network of agents that interact to achieve a user's particular purpose. Wayfound allows you to connect multiple agents into such a system and manage their interactions by creating actions. It also allows you to enhance multi-agent systems with tools and other [integrations](../settings/integrations/ "mention").

<div data-full-width="true"><figure><img src="../.gitbook/assets/Screenshot 2025-02-25 at 10.55.53 AM.png" alt=""><figcaption></figcaption></figure></div>

### Integrations

When an integration is activated in your organization, it will be visible in the **+ Add Action** drop-down menu. Wayfound currently offers the following integrations:

**Google Drive Sync**\
Keep your AI agents equipped with the latest information by integrating Google Docs and Sheets with Wayfound. This seamless sync ensures your agents always have up-to-date data, enhancing their accuracy and efficiency. Once connected, you can upload items into an agent's knowledge directly from Google Drive.

**Hubspot**\
Enable your AI agents to create HubSpot contacts when the chat participant provides their email address.

We plan to offer the following integrations and more in the near future: Box, HubSpot, Salesforce, and Web Search. If you have suggestions for additional integrations, please contact us.

### Updating and adding actions

You can update existing actions by clicking on them in the Actions page.

To create a new action, click the **+ Add Action** button below the existing ones. This opens a list of current agents in your your organization. Selecting an agent opens the **Set Up Agent Collaboration** window:

<figure><img src="../.gitbook/assets/Screenshot 2024-09-13 at 12.19.57 PM.png" alt=""><figcaption></figcaption></figure>

This window allows you to define how the agents should interact using intuitive, natural-language prompts. You can direct when the agent should contact another agent, when it should not contact the other agent, what relevant expertise the other agent has, and important caveats or limitations for the collaboration. For best results, we encourage 3-4 succinct and concrete sentences. Visit [#how-to-write-effective-behaviors](behavior.md#how-to-write-effective-behaviors "mention") for more help with natural-language prompts.

As always, we encourage you to [test-your-agents.md](test-your-agents.md "mention") when updating and adding actions.
