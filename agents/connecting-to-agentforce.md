# Connecting to Agentforce

The Salesforce Integration allows you to connect your Salesforce Agentforce agents with Wayfound, enabling comprehensive performance monitoring and management. This integration synchronizes your Salesforce agents with Wayfound's powerful analytics and evaluation tools, providing valuable insights to improve agent effectiveness.

### Requirements

You need to be an active Wayfound user and admin as well as a Salesforce user with permission to connect Salesforce via OAuth. In addition, the integration requires you to have access to Agentforce and Data Cloud on Salesforce.

### Connecting to Salesforce

To connect Salesforce to Wayfound, visit the **Agentforce** page in Wayfound's Settings tab:

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

In the Agentforce page, click <img src="../.gitbook/assets/Screenshot 2025-04-16 at 1.42.35 PM.png" alt="" data-size="line">. This will take you through Salesforce OAuth:

<figure><img src="../.gitbook/assets/image (17).png" alt="" width="243"><figcaption></figcaption></figure>

Once you have logged into Salesforce and authorized Wayfound, you will be taken back to Wayfound's Agentforce page:

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

### Salesforce Configuration

To connect Agentforce agents to Wayfound, agents must be enabled within Salesforce, in addition to agent analytics for Data Cloud. When Wayfound detects that each of these conditions are met, it will display a blue checkmark <img src="../.gitbook/assets/image (22).png" alt="" data-size="line"> next to them.

#### Enable Agentforce

If Agentforce is not turned on in Salesforce, visit the Agentforce Agents setup page by clicking <img src="../.gitbook/assets/Screenshot 2025-04-16 at 1.53.52 PM.png" alt="" data-size="line">. This will take you to the following page:

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Here, take the following actions:

1. Turn on Agentforce
2. Either create a **New Agent** or enable the **Agentforce (Default) Agent**

After taking these actions, refresh Wayfound's Agentforce settings page you will see a blue checkmark <img src="../.gitbook/assets/image (23).png" alt="" data-size="line">next to **Enable Agents**.

#### Enable Data Cloud

If Data Cloud is not enabled, click <img src="../.gitbook/assets/image (24).png" alt="" data-size="line"> to take you to visit the Einstein Feedback and Monitoring Setup page in Salesforce:

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**NOTE: Access to this page requires that you have already enabled Data Cloud**
{% endhint %}

Here, turn on **Agent Analytics**. It may take some time for Salesforce to update this setting. Return to Wayfound's Agentforce page to confirm that Agent Analytics have been activated. If so, Wayfound will display a blue check mark <img src="../.gitbook/assets/image (23).png" alt="" data-size="line"> next to **Enable Data Cloud**.

### Syncing Agents with Wayfound

Once Salesforce is correctly set up in Wayfound, you can **activate** your agents on the platform. To do so, activate **Supervise in Wayfound** for each agent you would like to sync with Wayfound:

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Once an Agentforce agent is activated, it appear on [the-agents-page.md](the-agents-page.md "mention") as any other agent. Now, you can add a role, goal, and guidelines to your agent to give the Wayfound AI Supervisor the context it needs for analyzing its performance:

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>



### Session Recordings with Wayfound

Every hour, Wayfound will sync with your Salesforce instance to pull your active agents' latest sessions.

{% hint style="warning" %}
Once the agent is activated it can take up to an hour for the first conversations to appear. In addition, conversations will only be pulled into Wayfound once they are in Data Cloud. This means it can take some time for conversations to appear. In the worst case, this may take several hours.
{% endhint %}

You can view your Agentforce Agents' session recordings in [recordings.md](../sessions/recordings.md "mention").

### Stop Syncing Agents

If you would like to disconnect an Agentforce agent from Wayfound, deactivate **Supervise in Wayfound** for the agent in Wayfound's Agentforce page. Disconnected agents can always be reconnected on this page. When reconnected, guidelines and previous sessions will be restored. You can always turn it back on again afterwards and you will not lose any guidelines or previous sessions synced to Wayfound.

{% hint style="info" %}
When an agent is reconnected, Wayfound will not download all sessions that have taken place during the period between the agent's deactivation and reactivation. Instead, Wayfound will only download agent sessions from the last six hours.
{% endhint %}

### Disabling Salesforce

To disconnect all Agentforce agents, click <img src="../.gitbook/assets/Screenshot 2025-04-16 at 2.15.25 PM.png" alt="" data-size="line"> in Wayfound's Agentforce page. This will deactivate all agents and Wayfound will no longer be able to sync any agents unless Salesforce is reconnected.

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>
