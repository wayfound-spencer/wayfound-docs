# Guidelines

Guidelines define the objectives and goals of your agent. When the AI Supervisor evaluates your agent's [performance](../supervisor/performance.md) and sends alerts based on its performance, it takes these guidelines into consideration. By adding unique guidelines for each agent, you can customize how it is supervised according to its particular role.

<figure><img src="../.gitbook/assets/Untitled (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Adding and updating guidelines

To add more guidelines, click the **+ Add Guideline** button below the list of current guidelines. You may add the following kinds:

<img src="../.gitbook/assets/Screenshot 2025-02-11 at 4.03.20 PM.png" alt="" data-size="line">**Prohibited Actions:** Specify actions the agent must never take, such as sharing sensitive information, making unauthorized promises, or accessing restricted systems.

<img src="../.gitbook/assets/Screenshot 2025-02-11 at 4.03.24 PM.png" alt="" data-size="line">**Prohibited Words:** Define specific terms or phrases the agent should not use. This includes inappropriate vocabulary, competitor names, or terminology that could cause confusion.

<img src="../.gitbook/assets/Screenshot 2025-02-11 at 4.03.28 PM.png" alt="" data-size="line">**Preferred Voice and Tone:** Establish the desired communication style through specific criteria like formality level, technical depth, and emotional resonance.

<img src="../.gitbook/assets/Screenshot 2025-02-11 at 4.03.36 PM.png" alt="" data-size="line">**Other Evaluation criteria:** Create custom metrics to assess agent performance based on the agent's particular role and goal.

You can update existing guidelines by clicking on their respective text field in the Guidelines page.

## Guideline Alerts

Wayfound allows you to set the importance of each guideline, giving you control over how often the AI Supervisor alerts you about the issues it identifies. Guidelines have two possible alert levels:

&#x20;<img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.22.03 AM.png" alt="" data-size="line">**Needs Review:** These are guidelines that, while important to follow, do not require urgent remediation if breached. The AI Supervisor will collect all potential "Needs Review" guidelines violations and alert uses about them once per day.

<img src="../.gitbook/assets/Screenshot 2024-11-18 at 11.17.36 AM.png" alt="" data-size="line"> **Needs Attention:** These are guidelines that may require an immediate response if breached. The AI Supervisor will alert users about "Needs Attention" guidelines as soon as it identifies a violation.

## Optimizing Your Guidelines

Guidelines are most effective when they:

**Focus on Specifics:** They focus on specific, measurable behaviors.

**Differentiate Severity:** They clearly differentiate between critical (needs attention) and important (needs review) issues.

**Provide Context:** They provide context about when exceptions are acceptable.

**Align with Priorities:** They align with your business priorities and user needs.
