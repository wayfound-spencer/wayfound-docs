# Agent Supervision Best Practices

Unlike conventional software which follows deterministic rules and procedures, AI agents use pattern recognition and reasoning to achieve their assigned goals. Wheareas traditional software operates within strictly defined parameters and produces predictable but narrow results, AI agents use nondeterministic functions to operate in more complex and dynamic environments. As an AI agent interaction unfolds, an agent can continuously adapt based on user interactions and leverage natural language understanding to interpret requests in a way that mirrors human comprehension.

While this nondeterministic nature of AI agents brings powerful flexibility, this approach to problem-solving introduces some unique management challenges. AI agents require continuous monitoring and improvement to ensure they remain aligned with your business goals and user expectations.

### Supervising Agents with Wayfound

Wayfound's AI Supervisor platform addresses these challenges by providing comprehensive monitoring and evaluation tools specifically designed for AI agents. The AI Supervisor:

* Analyzes agent-user interactions continuously and systematically
* Evaluates performance against your custom guidelines
* Identifies knowledge gaps and action failures
* Flags potential issues and alerts you for review
* Suggests specific improvements

The AI Supervisor performs all of these tasks at scale, allowing you to deploy your AI agents across thousands of simultaneous interactions. However, it's important to note that the Wayfound AI Supervisor is itself an AI agent. This means that using it effectively benefits from following AI agent best practices. This includes iterating on your approach through continuous monitoring and feedback.&#x20;

### Supervision is an ongoing process

As with any AI agent, the key to success with Wayfound’s AI Supervisor is continuous iteration. To ensure that it captures all potential issues with your agents, the Supervisor is tuned to prioritize false positives over false negatives. The Wayfound platform allows you to refine how the Supervisor evaluates agents over time, focusing its attention on what matters most and reducing false positives. To achieve this, we recommend that users:

**Review Alerts Regularly:** Check daily alerts for yellow flags (needs review) and address immediate red flags (needs attention) promptly. Use the Suggestions tab for specific recommendations.

**Provide Feedback on Guidelines Application:** When the AI Supervisor flags a guideline violation that doesn't align with your expectations, use the User Feedback function directly from session transcripts. Clarify your intent to help the Supervisor better interpret guidelines in future assessments. Visit the [user-feedback.md](user-feedback.md "mention") documentation to learn more about providing feedback.

**Refine Guidelines:** If you're receiving too many alerts, consider changing some red (needs attention) flags to yellow (needs review) if they're not critical. Provide more context in guidelines to help the Supervisor understand acceptable exceptions and adjust guideline priorities based on business impact.

**Address Knowledge Gaps:** Prioritize knowledge gaps that appear frequently and update your agent's knowledge base in response to identified gaps. Review transcripts where knowledge gaps occur to understand the context.

**Improve Tool Performance:** Monitor tool failure rates and patterns, optimize failing tools based on error messages and failed attempts, and consider alternative approaches for consistently problematic actions.

### Measuring Progress

We recommend that users track the following key indicators to measure improvement:

**Alert Reduction:** Reduction in legitimate alerts over time.

**Satisfaction Improvement:** Improved user satisfaction scores.

**Knowledge Enhancement:** Decreased knowledge gaps.

**Action Optimization:** Higher action success rates.

Remember that supervision is an ongoing process. As your business evolves and user needs change, it is important to continue to refine your approach to agent supervision--just as you should refine the supervision and management of any part of the business.
