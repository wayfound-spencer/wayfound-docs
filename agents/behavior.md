---
description: >-
  Behaviors let you control your agent's interactions with users with intuitive,
  natural-language prompts.
---

# Behavior

{% hint style="warning" %}
Behaviors are only available for agents built in the Wayfound platform.
{% endhint %}

<div data-full-width="true"><figure><img src="../.gitbook/assets/Screenshot 2025-02-25 at 10.38.34 AM.png" alt=""><figcaption></figcaption></figure></div>

Wayfound offers behaviors as an easy and effective approach to prompt engineering. Behaviors allow you to break down long prompts into smaller components that you can test and iterate. By adding specialized behaviors your agent, you can ensure that it responds appropriately and delivers the best possible experience.

Agents come pre-populated with the following four behaviors:

* You are a friendly AI Agent that helps users.
* You should have a positive attitude and be helpful.
* You should only use known information and not guess.
* Only respond with information related to the Agent topic.

These behaviors are helpful for most applications, but they can be removed.

### Updating and adding behaviors

You can update existing behaviors by clicking on them in the Behavior page.

To add more behaviors, click the **+ Add Behavior** button below the list of current behaviors. You may add the following kinds of behaviors:

<img src="../.gitbook/assets/Screenshot 2024-09-19 at 10.01.55 AM.png" alt="" data-size="line">**If/then statement:** Define specific actions for the agent to take in response to particular user inputs or situations.

<img src="../.gitbook/assets/Screenshot 2024-09-19 at 10.02.00 AM.png" alt="" data-size="line">**Personality/tone guidance:** Customize the agent's communication style, such as formal, casual, or empathetic.

<img src="../.gitbook/assets/Screenshot 2024-09-19 at 10.02.05 AM.png" alt="" data-size="line">**Conversation flow:** Guide how the agent conducts dialogues, including follow-up questions and topic transitions.

<img src="../.gitbook/assets/Screenshot 2024-09-19 at 10.02.10 AM.png" alt="" data-size="line">**Call to action:** Instruct the agent to encourage specific user actions, like contacting support or using certain features. Encourage the agent to provide the appropriate links for taking these actions.

<img src="../.gitbook/assets/Screenshot 2024-09-19 at 10.02.17 AM.png" alt="" data-size="line">**Restrictions/limitations:** Set boundaries on what the agent can say or do to ensure appropriate interactions.

<img src="../.gitbook/assets/Screenshot 2024-09-19 at 10.02.22 AM.png" alt="" data-size="line">**Custom Command:** Create unique behaviors tailored to your agent's specific purpose or domain.

As always, we encourage you to [test-your-agents.md](test-your-agents.md "mention") when updating and adding behaviors. Wayfound makes this easy by offering a chat interface on the right-hand side of the screen. After you update or add behaviors, you can click <img src="../.gitbook/assets/Screenshot 2024-09-18 at 2.42.38 PM.png" alt="" data-size="line"> reset at the top of the chat window to update the agent and test it. Testing your agents is a critical step to take before publishing them. Over time, we also recommend adding behaviors suggested by the Wayfound [suggestions.md](../sessions/suggestions.md "mention") tool.

Visit [improving-agent-performance.md](../improving-agent-performance.md "mention") for tips on writing good behaviors.

{% hint style="info" %}
Here are some more resources about prompt engineering:

* OpenAI's [Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
* Anthropic's [Prompt Engineering Overview](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
{% endhint %}
