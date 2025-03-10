# The Agents Page

Wayfound allows you to create and manage a network of specialized agents. Each agent can perform a focused task, and agents can collaborate to accomplish more complex tasks. The Agents tab displays a list of all agents in your organization. It also allows you to build and configure new ones.



<figure><img src="../.gitbook/assets/Screenshot 2024-12-03 at 2.24.51 PM.png" alt=""><figcaption></figcaption></figure>

### View and manage current agents

Opening the agents tab displays a table of agents created for your organization. Users can **sort** agents by name, platform, last updated date, last published date, and status. Users can also <img src="../.gitbook/assets/Screenshot 2024-09-18 at 2.35.20 PM.png" alt="" data-size="line">**search** for specific agents and <img src="../.gitbook/assets/Screenshot 2024-09-18 at 2.36.40 PM.png" alt="" data-size="line">**filter** by column using buttons in the table's upper-right corner.

In the agents table, the **Actions** column contains a menu of actions that can be opened by clicking the ![](<../.gitbook/assets/Screenshot 2024-10-03 at 11.50.27 AM.png>)button. Within this menu, you can ![](<../.gitbook/assets/Screenshot 2024-10-03 at 11.49.43 AM (1).png>)**view the published agent** in a new browser tab, ![](<../.gitbook/assets/Screenshot 2024-10-03 at 11.49.47 AM.png>)**view agent analytics,** and ![](<../.gitbook/assets/Screenshot 2024-10-03 at 12.00.44 PM.png>)**activate** or ![](<../.gitbook/assets/Screenshot 2024-10-03 at 11.49.51 AM.png>)**deactivate agent**. Activating an agent will publish it, making it publicly available. When an published agent is deactivated, it will remain on the Wayfound platform but will no longer be publicly available until reactivated.

### Onboard an existing agent

Wayfound lets you connect existing external agents to the platform. This includes those built on popular frameworks like LangChain. Adding an agent to Wayfound allows you to track, monitor, and manage it using the Wayfound platform. To connect an agent, you can use the [Wayfound Manager SDK](connection.md) to import recorded conversations from your external agent.

To onboard an existing agent:

1. Click <img src="../.gitbook/assets/Screenshot 2024-11-25 at 12.27.06 PM.png" alt="" data-size="line"> at the top-right corner of the Agents tab.
2. A new menu will appear. Name the agent and explain its role and goal. This information will inform the AI manager's performance evaluation of this agent. Click **Connect**.

<figure><img src="../.gitbook/assets/Screenshot 2025-03-10 at 11.22.47 AM.png" alt=""><figcaption></figcaption></figure>

### Create a new agent

If you do not have an agent already built using a third-party framework, you can create a new one in Wayfound. To create a new agent, click <img src="../.gitbook/assets/Screenshot 2024-11-25 at 12.27.29 PM.png" alt="" data-size="line"> . This opens a new menu where you can name your agent and select between an OpenAI and Anthropic model to power the agent. Remember: the name you select for the agent is the name that users will see.

<figure><img src="../.gitbook/assets/Screenshot 2024-09-11 at 2.01.15 PM.png" alt="" width="375"><figcaption></figcaption></figure>

Clicking **Create Agent** brings you to your new agent's [knowledge.md](../knowledge.md "mention") page, where you can continue setting up the agent.

For more documentation on building agents in wayfound, [contact us](https://www.wayfound.ai/get-started).
