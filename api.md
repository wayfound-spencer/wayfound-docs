# API

Wayfound offers APIs to connect your agents to the platform. Current APIs allow you to collect information about agents, manage chat recordings, and run tests.

You can generate an API key on the **API tab** in the **Settings** page. Access to this page requires admin permissions on the Wayfound platform.

Currently avalaible APIs include the following:

**Get Agents:** Returns an array of all Published agents.

**Get Agent:** Returns a single Published agent.

**Create New Agent:** Create a new agent. The agent will be unpublished.

**Update Agent:** Update an agent's name, role, goal, or guidelines

**Create Completed Recording:** Create a recording after a complete agent session has concluded and all messages have been sent and received. Processing of the recording will occur immediately.

**Create Active Recording:** Create an initial recording for an active and ongoing Agent session. This recording can be updated as more messages are sent and received. Processing of the recording will occur approximately 5 minutes after the last update to the recording.

**Update Active Recording:** Update an active recording by sending the current messages array. Processing of the recording will occur approximately 5 minutes after the last update to the recording.

**Initiate Agent Test Run:** Initiates a new Test Run for the Agent specified. You must also specify using the draft version of the agent or the published version. The response includes the initial opening phrase from the Agent.

**Send Messages to Test Run:** Sends messages to the specified Test Run. The messages are processed by the Agent and the Agent response is included in the messages array of the response.

[Learn more about implementing Wayfound's APIs here](https://wayfound-api.readme.io/reference/get-agents)

