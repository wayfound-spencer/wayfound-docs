# Performance

The Performance tab provides a comprehensive overview of your individual agents' performance, offering insights and areas for improvement. It is powered by Wayfound's AI Supervisor, which continually monitors your active agents. The Wayfound AI Supervisor is powered by state-of-the-art LLMs. It currently uses OpenAI's gpt-5 model to analyze agent performance.

This view is designed to help you quickly understand the strengths and weaknesses of your agents and identify directions for improvement.&#x20;

<figure><img src="../.gitbook/assets/Untitled (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The Performance tab provides insights for all agents in the organization with at least 5 user interactions. The performance of a given agent can be displayed  by clicking  <img src="../.gitbook/assets/Screenshot 2024-09-25 at 10.41.29 AM.png" alt="" data-size="line"> or hidden by clicking <img src="../.gitbook/assets/Screenshot 2024-09-25 at 10.41.36 AM.png" alt="" data-size="line"> next to each agent's name.&#x20;

## **Assessment Outcomes**

The AI Supervisor evaluates the performance of your agents by reading and rating its interactions with users. The overall results are displayed on the Performance tab to the right of each agent's name. Possible outcomes include:

<img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.16.46 AM.png" alt="" data-size="line">**Hot to go!:** The agent is meeting expectations in its interactions. However, the AI Supervisor can still raise potential issues and provide suggestions for improvement.

<img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.22.03 AM.png" alt="" data-size="line">**Needs review:** The agent's performance is satisfactory, but there are areas that require closer attention and potential improvement. The AI Supervisor will flag an agent as "Needs review" when any of the following are triggered:

* User Rating 1-3
* Negative sentiment
* Agent Goal was not successful
* 1 or 2 or Knowledge Gaps
* [guidelines.md](../agents/guidelines.md "mention") Violation where user specifies a "Needs review" priority

<img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.17.36 AM.png" alt="" data-size="line">**Needs attention:** the agent is facing significant challenges or issues that require immediate focus and resolution. The AI Supervisor will flag an agent as "Needs attention" when any of the following are triggered:

* Action Failure
* 3+ Knowledge Gaps
* [guidelines.md](../agents/guidelines.md "mention") Violation where the user specifies a "Needs attention" priority

More information can be accessed using the link to the [suggestions.md](../sessions/suggestions.md "mention") tab, which provides specific recommendations for improvement.

## **Assessment components**

During its review of agent performance, the AI Supervisor identifies each agent's knowledge gaps, considers user satisfaction scores, and searches transcripts for specific issues. These components are all displayed in the tab.

### **User Satisfaction**

Wayfound collects ratings given by users at the end of their interactions with agents. It summarizes them here with an overall average score and a distribution of scores. Click on the summary of user satisfaction scores to view a detailed breakdown of sessions by score. For each session, click <img src="../.gitbook/assets/Screenshot 2024-12-16 at 11.29.44 AM.png" alt="" data-size="line">to view the corresponding transcript.

<figure><img src="../.gitbook/assets/Screenshot 2025-02-25 at 11.07.55 AM.png" alt="" width="432"><figcaption></figcaption></figure>

### **Knowledge Gaps:**

As part of its assessment, the AI Supervisor identifies the knowledge gaps that emerged in the agent's recent interactions. The Performance tab displays a graph of recordings that indicate knowledge gaps as a share of total recordings. Clicking the graph displays specific knowledge gaps on the right-hand side of the page:

<figure><img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.41.14 AM.png" alt="" width="375"><figcaption></figcaption></figure>

Click each theme to expand with more details with summaries of relevant sessions. For each session, click <img src="../.gitbook/assets/Screenshot 2024-12-16 at 11.29.44 AM.png" alt="" data-size="line">to view the corresponding transcript.

### **Guideline Violations:**

The AI Supervisor assesses the performance of each agent according to the custom [guidelines.md](../agents/guidelines.md "mention") you set for it. The performance tab displays the count and percentage of recordings where the agent was compliant vs in violation of the guidelines. Clicking on this chart provides more detail for each guideline, along with example sessions for each guideline violation. For each example session, click <img src="../.gitbook/assets/Screenshot 2024-12-16 at 11.29.44 AM.png" alt="" data-size="line">to view the corresponding transcript.

<figure><img src="../.gitbook/assets/Screenshot 2025-02-25 at 11.06.33 AM.png" alt="" width="431"><figcaption></figcaption></figure>

Users can provide feedback to improve the AI Supervisor's application of agent guidelines by opening a session containing a guideline violation. See [user-feedback.md](../user-feedback.md "mention") for more information.

### **Action Failures:**

The AI Supervisor monitors your agents' action calls and calculates their success rates. Click the overall summary of action failures to open a more detailed view of failure rates by action. Each action links to sessions where that action was called.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2025-02-25 at 11.06.50 AM.png" alt="" width="433"><figcaption></figcaption></figure>

For each example session, click <img src="../.gitbook/assets/Screenshot 2024-12-16 at 11.29.44 AM.png" alt="" data-size="line">to view the corresponding transcript. Session transcripts display where an action was called. Click the action to show more detail about the request:

<figure><img src="../.gitbook/assets/Screenshot 2024-11-18 at 12.04.38 PM.png" alt="" width="375"><figcaption></figcaption></figure>

### **Potential issues:**

As part of its review, the AI Supervisor identifies potential issues in the agent's interactions with users. These issues may concern the agent's behaviors or the overall outcome of its interactions. The supervisor includes references to specific recordings that demonstrate these issues. Clicking on a reference opens it on the right side of the page:

<figure><img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.56.39 AM.png" alt="" width="375"><figcaption></figcaption></figure>

As shown, each recording is also given a status, an explanation of that status, and suggestions for improvement based on the individual interaction. Below the suggestions is the transcript itself.

### Follow-Up Analysis

The performance tab displays a chat window where you can interact with the AI Supervisor agent for additional analysis. You can probe further on any of the insights it provides or ask questions about other aspects of the agent's performance. This allows the AI Supervisor to explain its assessment, enhancing your understanding and confidence in its analysis.

Based on the feedback it provided, the AI Supervisor suggests custom follow-up questions. These suggestions are found below the key topics. In addition to the suggested questions, you can also prompt the AI Supervisor to:

* Provide more details or evidence for a specific insight
* Compare this agent's performance to similar agents in the organization
* Suggest ways to leverage and expand on the highlighted strengths
* Offer recommendations for resolving specific issues
