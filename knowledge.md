---
description: >-
  Knowledge allows you to add and edit the content used by the agent during its
  interactions.
hidden: true
---

# Knowledge

{% hint style="warning" %}
The Knowledge tab is only available for agents built on Wayfound
{% endhint %}



<figure><img src=".gitbook/assets/Screenshot 2024-09-11 at 2.13.19 PM.png" alt=""><figcaption></figcaption></figure>

### Default Content

All new agents include the following four elements in their knowledge base:

**Agent Name**: This is the name users see when interacting with the agent. It is also the name used to identify the agent across the Wayfound platform.

**Greeting:** The agent uses the greeting as its opening message during new conversation with users. The greeting allows you to set the conversation's direction with an opening question or introduction. The greeting comes pre-populated by default but can be edited at any time.

**Starter Prompts:** Starter prompts serve as suggestions for users during new conversations. Users can choose one of them or type their own. A good starter prompt is a question or request that the agent has been designed to address. The platform allows for up to four starter prompts.

**Overview:** This is a high-level description of the Agent and its functionalities, context, and purpose. Here is where you can describe the Agent's desired role.

### Updating and adding content

You can update all existing content by selecting it in the knowledge page.

To add more content to your agent's knowledge, click the **+ Add Content** button at the bottom-left corner of the knowledge tab. Wayfound allows you to add various kinds of content as separate subsections.

With the <img src=".gitbook/assets/Screenshot 2024-09-18 at 2.38.50 PM.png" alt="" data-size="line">**text** and <img src=".gitbook/assets/Screenshot 2024-09-18 at 2.38.54 PM.png" alt="" data-size="line">**document** subsections, the agent can directly read the content you add.

The agent can share content uploaded in <img src=".gitbook/assets/Screenshot 2024-09-18 at 2.38.58 PM.png" alt="" data-size="line">**image** and <img src=".gitbook/assets/Screenshot 2024-09-18 at 2.39.01 PM.png" alt="" data-size="line">**video** subsections with users. These subsections include space for describing when the agent should show this content.

With a <img src=".gitbook/assets/Screenshot 2024-09-18 at 2.39.05 PM.png" alt="" data-size="line">**URL** subsection, you can upload content from web pages.

{% hint style="info" %}
Note that agents cannot navigate across multiple pages in a website. To upload content from multiple pages, you can upload each page separately.
{% endhint %}

Wayfound also allows you to upload documents directly from <img src=".gitbook/assets/Screenshot 2024-10-02 at 1.44.54 PM.png" alt="" data-size="line">**Google Drive** using the Google Drive integration.&#x20;

### The importance of adding knowledge

#### Enhancing capabilities

The depth and breadth of your agent's knowledge directly impact its performance. When creating or updating an agent, we recommend you consider all possible use cases and the knowledge an agent would need to successfully address each. Depending on the use case, some possible sources of knowledge include:

* Company web pages
* Product images and videos
* Pricing and product feature information
* Product FAQs and support documentation
* Company policy documentation
* Customer feedback data and reports
* Internal training materials

#### Increasing reliability

Since their initial release in 2022, commercially available large language models have grown increasingly reliable in their outputs. From time to time, however, these models can still hallucinate, or create outputs that do not accurately reflect reality. Wayfound agents are designed to minimize the chance of hallucinations. You can further reduce the chance of hallucinations by adding more content to an agent's knowledge base. Giving an agent all the information it might need to perform the desired tasks will enable it to accurately represent your company, products, and services.

Just as we encourage you to create agents with deep knowledge bases, we also recommend creating agents for specialized applications. Addressing a set of use cases with a team of specialized agents is more effective and reliable than trying to cover all use cases with a single agent. Wayfound helps you coordinate specialized agents in the [actions.md](agents/actions.md "mention") tab.

After adding or updating content, you should [test-your-agents.md](agents/test-your-agents.md "mention") to check for possible hallucinations. Over time, you can fill the knowledge gaps identified by the Wayfound [suggestions.md](sessions/suggestions.md "mention") tool.

