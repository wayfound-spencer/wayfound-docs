# HubSpot Integration

Wayfound's HubSpot integration enables your AI agents to automatically create HubSpot contacts when chat participants provide their email addresses. Additionally, chat transcripts are attached as notes to the corresponding contacts in your HubSpot account, creating a comprehensive record of all conversations between your contacts and AI agents.

### Setup Instructions

Setting up the HubSpot integration in Wayfound requires the following:

* A Business or Enterprise Wayfound Plan
* Admin-level permissions in Wayfound
* Access to your organization's HubSpot account

To add HubSpot to your organization in Wayfound, take the following steps:

1. **Authentication Setup** Begin by navigating to Settings, then select the Authentication tab. Look for the HubSpot icon and click it to start the authentication process. You'll be guided through the steps to connect your HubSpot account. For more detail, visit [Integrations](./).
2. **Enable HubSpot Actions** Next, return to Settings and select the Actions tab. Find and click the HubSpot button to add HubSpot functionality to your organization.
3. **Create or Configure an Agent** To set up an agent, find the Agents Tab in the left-hand navigation panel. You can either click the "New Agent" button to create a new agent or select an existing one to modify. For more detail, visit [the Agents Tab](../../agents/the-agents-page.md).
4. **Add the HubSpot Action to Your Agent** Once your agent is configured, go to the Actions tab in Agent Settings. Look for the "**+ Add Action**" button and click it. From the list of available actions, select HubSpot to enable the integration for this agent. For more detail, visit [Actions](../../agents/actions.md).

### Testing the Integration

Once the HubSpot action has been added to your agent, it can use the action during its conversations. Here's how to test the integration:

1. Start a chat with your configured agent and provide it a test email address
2. Look for the "Create HubSpot contact" confirmation in the chat transcript. It looks like this: <img src="../../.gitbook/assets/Screenshot 2024-10-25 at 10.12.54 AM.png" alt="" data-size="line">
3. Wait approximately 20 minutes for chat processing to complete
4. Check your HubSpot account - the new contact should be added with the chat transcript will attached as a note
