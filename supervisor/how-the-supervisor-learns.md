# How the Supervisor Learns

The AI Supervisor does more than grade each session in isolation. For every agent it maintains a living understanding — what the agent is for, where it struggles, and how your team wants its guidelines applied — and it uses that understanding to evaluate every new session. The result is an evaluation layer that gets more accurate and more tailored to your organization the longer it runs.

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

### Evidence memos

Behind the scenes, the Supervisor keeps a small set of **evidence memos** for each agent — concise notes it updates as new sessions come in:

* **The agent's purpose and scope** — what it's meant to do.
* **What it does well** — strengths worth reinforcing.
* **Recurring failure patterns** — issues that show up again and again.
* **Knowledge gaps** — topics the agent repeatedly lacks information on.
* **Evaluation principles** — the standards the agent should be judged by, including anything your team has clarified through feedback.

Because these memos accumulate patterns across many sessions, the Supervisor recognizes recurring problems instead of rediscovering them one transcript at a time.

### The evaluation rubric

From those memos and your published guidelines, the Supervisor distills a single **evaluation rubric** — a concise grading guide it applies to every future session. The rubric captures:

* **Intent** — a short statement of what the agent is for.
* **Guideline interpretation** — for each guideline, how your organization has learned to apply it in practice. Learned interpretation can only _narrow_ a guideline (make it more precise), never broaden it beyond what you wrote.
* **Broader patterns** — cross‑cutting signals to watch for, including any open potential issues.

The rubric stays current automatically: it's re‑distilled whenever the Supervisor learns something new or when you change your guidelines.

### The feedback loop

Your input is what makes the Supervisor smarter. Three things teach it:

1. **Teaching from a session** — correcting or reinforcing a verdict on a transcript.
2. **Answering open questions** — resolving cases the Supervisor flagged as ambiguous.
3. **Triaging potential issues** — promoting patterns into guidelines, confirming expected behavior, or dismissing false positives.

Each of these updates the evidence memos, which re‑distill the rubric, which changes how the next session is scored. The Supervisor consolidates this learning continuously in the background, so improvements show up in subsequent assessments without any manual step.

### Auditability

Everything the Supervisor uses to judge your agents is visible to organization admins in the **Memos** tab: the current evaluation rubric, the evidence memos behind it, and a version history that lets you trace any change back to the feedback and observations that caused it.

\[screenshot: rubric version history / diff view]

### Availability

Continuous learning is enabled for your organization and is available to organization admins. It's on by default for new organizations and is being rolled out across existing ones. If you're an admin and don't see the **Memos** and **Review** tabs yet, contact Wayfound to have it enabled. Until it's active, the AI Supervisor continues to provide session‑by‑session assessments as described in Performance.
