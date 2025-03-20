---
hidden: true
---

# Improving Agent Performance

Today's AI agents, including those built and managed on Wayfound, are powered by large language models. On one hand, these models take everyday natural language as inputs, enabling you to control their behavior without writing code. On the other hand, large language models are nondeterministic, meaning that they lack a one-to-one relationship between their inputs and outputs. Just like humans, every time you interact with a large language model, you can expect a slightly different outcome.

## Three tools for controlling agents

Wayfound provides three complementary tools for shaping and enhancing your AI agents' performance:

1. [**Behaviors**](agents/behavior.md) serve as specific instructions for individual agents, controlling how they interpret and respond to user interactions. Behaviors define exactly how an agent should handle specific situations, from breaking down complex explanations into steps to knowing when to escalate issues.
2. [**Global Directives**](manager/alignment.md) establish organization-wide principles that align all agents with your company’s mission and values. These directives create consistency across your AI network, ensuring that every agent interaction reflects your brand voice and organizational approach to problem-solving.
3. [**Knowledge**](knowledge.md) provides the factual foundation that agents can reference, determining not just what information they can share, but how precisely they can assist users. Comprehensive knowledge enables agents to provide accurate, context-appropriate responses.

\> These tools work in a hierarchical relationship: Global Directives establish your organizational foundation, Behaviors implement these principles through specific agent actions, and Knowledge provides the substance that makes these interactions meaningful and accurate. When modifying agent behavior, carefully consider which tool best suits your goal, and ensure your controls work together rather than sending conflicting signals.

Maximizing agent performance requires thoughtful implementation of all three control tools through continuous testing and refinement. While controlling AI agents isn't yet an exact science, following these principles will help you create more effective and reliable AI interactions.

## Mixing effective Behaviors and Global Directives

Use behaviors to control the unique, context-specific actions of individual agents. When you want all agents to share a common characteristic or approach, implement it as a Global Directive instead. This distinction helps create a clear hierarchy of control while maintaining consistency where needed.

Since behaviors operate on the level of individual agents, they should be tailored to the particular context and purpose of each agent. The most effective behaviors are context-specific. Instead of trying to change the model's overall tendencies, focus on what you need for your current task. For example:

* "When asked for directions, please prioritize completeness over brevity"
* "When providing a summary, focus on key points and keep it under 3 paragraphs"

These prompts will produce more consistent outcomes than alternatives like "Always be more concise" or "Be careful and cautious." The power of behaviors lies in their specificity – instead of broad directives like "be helpful," create precise instructions that define what helpful means in your context, such as "proactively offer relevant documentation links" or "suggest related features based on user questions."

### Tips for writing Behaviors and Global Directives

* **Be specific and precise**: Clearly define the desired behavior, goals, or tasks using simple, straightforward directives. Avoid ambiguity or vague instructions that could be misinterpreted.
* **Provide context**: Give relevant background information to help the agent respond to specific situations and make appropriate decisions.
* **Define constraints and limitations**: Clearly state any boundaries or restrictions the agent should adhere to.
* **Specify the desired tone and style**: Describe the desired tone (e.g., formal, casual, empathetic) and style (e.g., comprehensive, succinct) for the agent's responses.
* **Specify the desired response format**: If you need a particular output format for the agent's designated purpose, clearly describe it (e.g., JSON, markdown, bullet points).
* **Encourage links and citations**: When appropriate, instruct the agent to reference its sources and direct users to relevant resources or contacts. When adding a behavior like this, make sure the required resources are added to the agent’s knowledge base!
* **Stress the importance**: If certain behaviors are particularly important, emphasize it with language like "IMPORTANT:," "ALWAYS," or "NEVER."

## Creating knowledgeable agents

In addition to Behaviors and Global Directives, you can indirectly control your agents using the Knowledge feature. The depth and precision of your agent's knowledge directly impacts its reliability and effectiveness. To minimize hallucinations and ensure accurate responses, include all information your agent might need in its specific context – even details that seem obvious or rarely needed. For example, if your agent discusses pricing, include not just the prices but also payment terms, refund policies, and seasonal variations. If it handles technical support, provide detailed troubleshooting steps, known issues, and their resolutions. This comprehensive approach helps the agent maintain accuracy and avoid making assumptions or providing incomplete information.

Your knowledge design should mirror your agent's intended conversation patterns. If you want your agent to provide step-by-step guidance, include detailed procedural documentation with specific steps, examples, and edge cases. If you expect your agent to escalate issues appropriately, clearly define escalation paths with specific contact information, roles, and the situations that warrant escalation. For specialized topics, include terminology definitions and contextual explanations that help the agent communicate at the right level of expertise for your users. Remember that your agent can only be as precise and helpful as the knowledge you provide – think through common user scenarios and ensure your agent has the detailed information needed to handle each one effectively.

### Managing the complexity of AI systems

Large language models are powerful tools, but just like humans, today’s models cannot achieve perfect behavior across all situations. Making the models work for your particular applications requires recognizing and working with this limitation, focusing on the models’ current strengths rather than trying to compensate for their shortcomings. For example, it is best to:

* Create a network of focused AI agents, each expertly configured for specific tasks rather than attempting to build all-purpose agents
* Tailor each agent's behaviors to its specific role and context, ensuring its responses align with user expectations in that particular domain
* Focus on achieving reliable, useful outcomes rather than pursuing perfect personality consistency or human-like behavior
* Consider which aspects of agent behavior should be consistent versus where natural variation is acceptable or even beneficial

**Since AI language models are complex systems, you cannot isolate and modify single traits without affecting others**. Agent responses emerge from deep interactions within the model's training. When attempting to make specific adjustments to Behaviors, Global Directives, or Knowledge, always test the model's responses across various scenarios to identify any unintended changes. For example, if you prompt for more concise responses, test not just the brevity but also the accuracy and completeness of information, for example, and the handling of edge cases.

\
\
