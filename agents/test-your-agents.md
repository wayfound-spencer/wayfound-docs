# Test your agents

Testing AI agents is a critical step in the agent creation and deployment process. Thorough testing ensures that your agent performs as intended, provides accurate information, and delivers a positive user experience.

### How to test agents in Wayfound

Wayfound provides multiple tools for testing and improving agents. When creating or updating a draft agent, the platform displays a playground interface for interacting with it. This interface appears on the right-hand side of all tabs in the agent page.

<div data-full-width="true"><figure><img src="../.gitbook/assets/Screenshot 2024-09-13 at 11.44.44 AM.png" alt=""><figcaption></figcaption></figure></div>

This enables the iterative testing of AI agents. For example:

* In the [knowledge.md](knowledge.md "mention") tab, you can assess whether the agent has all required knowledge for the task at hand and fill in any possible gaps by adding content.&#x20;
* In the [behavior.md](behavior.md "mention") tab, you can confirm whether the agent's actions, style, and voice corresponds with its intended purpose and add or adjust behaviors as needed.
* In the [actions.md](actions.md "mention") tab, you can check whether the agent collaborates with other agents or employs tools and integrations in the correct circumstances.

The draft agent testing interface includes three functions at the top-right corner:

<img src="../.gitbook/assets/Screenshot 2024-09-18 at 2.42.30 PM.png" alt="" data-size="line">**Debug Mode** to display badges when the agent performs an action

<img src="../.gitbook/assets/Screenshot 2024-09-18 at 2.42.34 PM.png" alt="" data-size="line">**Copy to clipboard** to save the conversation elsewhere

<img src="../.gitbook/assets/Screenshot 2024-09-18 at 2.42.38 PM.png" alt="" data-size="line">**Reset** to start a fresh interaction

### Key areas to test

When testing your AI agent, pay attention to the following aspects:

* **Accuracy:** Ensure the agent provides correct and up-to-date information. Confirm the responses' truthfulness to minimize the risk of hallucinations.
* **Relevance, language and tone:** Check if responses are pertinent to the user's query and context. Ensure that the agent communicates in alignment with your company voice and is appropriate for the intended audience.
* **Consistency:** Verify that the agent maintains consistent information and tone across interactions. To do so, test multiple ways of writing the same query.
* **Ability to handle edge cases:** Test the agent's ability to handle unexpected or complex queries. Determine whether an agent appropriately handles a given query on its own, calls another agent, or directs the user to a human for further support.
* **Integrations:** If applicable, test how well the agent integrates with other systems or platforms.
* **Security and Privacy:** Verify that the agent adheres to your company's data protection standards and doesn't disclose sensitive information unless appropriate.

### Testing your agents at scale

Wayfound also supports the automated testing of agents at scale using an API. [Learn more about the API here](https://wayfound-api.readme.io/reference/initiate-agent-test-run). In addition, Wayfound offers a testing partnership with [Okareo](https://okareo.com).&#x20;

### Monitoring and improving agents over time

In addition to the manual testing of draft agents, Wayfound Sessions tab provides tools for monitoring and improving agents after their deployment. For example, the [suggestions.md](../sessions/suggestions.md "mention") tab provides suggested behaviors and flags knowledge required. The [recordings.md](../sessions/recordings.md "mention") provides a record of users' interactions along with key metrics.
