# Getting Started

## **Planning and Building Your Agent**

Before building your agent, carefully plan its purpose and requirements:

1. **Define your use case**: Focus on specific, single-task applications. Keep the scope narrow and let other agents or humans handle different tasks in a larger network of intelligence.
2. **Set clear objectives**: Identify the desired outcomes from agent interactions.
3. **Plan capabilities**: Determine the knowledge, behavior, and tools your agent needs to complete the desired tasks and how to equip the agent with them.
4. **Build your agent**: Use one of many available agent builders like LangChain to build your agent. Once your agent is built, you can connect it to Wayfound.

## Connecting your agents to Wayfound

1. **Add your agent to the platform**: Navigate to [the-agents-page.md](agents/the-agents-page.md "mention"), click **+ Supervisor Agent**, and give it a name, role and goal.
   1. The **Name** is how the supervisor is referenced throughout Wayfound
   2. The **Role** describes the context in which the agent is running in your product such as how it interacts with users or describing where it sits within an agent workflow.  The Wayfound Supervisor uses this context as part of the session analysis process.
   3. The **Goal** describes the objective of the agent for each session run.  This should be a verifiable goal.  It is important that the goal has a clear success criteria that can be evaluated with the session data being provided to Wayfound.
2. **Create an API Key**. Users with admin status can create an API key on the [api.md](api.md "mention") page.
3. **Integrate your agent**: Add Wayfound to your external agent using the [connecting-agents.md](agents/connecting-agents.md "mention")

## Agent Success Criteria

1. **Guidelines** describe the success criteria for how your agents accomplish their **Goal.**  See the agent [guidelines.md](agents/guidelines.md "mention") page for more information. &#x20;
2. For Guidelines that apply to all agents see the [global-guidelines.md](supervisor/global-guidelines.md "mention")page.&#x20;
3. The Supervisor will use the Guideline definitions to roll up any violations of the guidelines across all sessions in it's nightly analysis.

## Supervisor Alignment

1. It is important to test your agent's Role, Goal, and Guideline definitions to ensure that the Wayfound Supervisor understands your guideline intent with your own session data.
2. We suggest that you use [test-mode.md](agents/test-mode.md "mention") to upload a representative set of sessions that demonstrate both successful and unsuccessful session sessions.  We suggest starting adding one guideline at a time while going through the define/test iteration process.
3. As part of the Test Mode analysis you will be setting your expected outcome of guidelines and be able to test multiple iteration runs against your test sessions to ensure that the agent's role, goal, and guidelines produce expected and reliable results.  This is a sandboxed environment that will not impact your production environment.

**Note:** This process is a fantastic way to start any new agent project.  Even if you are early in the technical implementation of your agent, you can generate sample session data, build guidelines, and label each session/guidleine permutation with your expected output.  You can think of this as "test driven development" for AI agent building where the business owner of the AI agent sets the success criteria that empowers both the business owner and engineering team with a common goal to work towards.

## Supervise your agent

Once your agent is connected you can use the AI Supervisor to monitor and improve its performance on the [performance.md](supervisor/performance.md "mention") page.

1. **Knowledge:** check knowledge gaps and fill them if necessary by adding missing information
2. **User Satisfaction:** Check user satisfaction scores and investigate any low ratings
3. **Issue management:** Examine potential issues raised by the AI Supervisor
4. **Follow-up analysis:** Delve deeper into agent performance by chatting with the AI Supervisor. You can start with questions recommended by Wayfound.

## **Using advanced features**

Once your agents are running and managed, you can leverage Wayfound's full capabilities such as:

1. **Interaction-level analysis**: Use Recordings to review specific agent interactions.
2. **Engagement tracking**: Monitor Link clicks during agent interactions.
3. **Cross-agent collaboration**: Set up agent meetings to produce organizational insights.

