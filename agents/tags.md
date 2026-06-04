# Tags

## How Tagging Works

Tags are labels Wayfound applies to your agent's sessions to capture what each conversation was about. A session might be tagged `PRICING-QUESTION`, `BILLING-ISSUE`, or `FEATURE-REQUEST` — whatever categories matter to your business.

Once your sessions are tagged, you can:

* **Filter and search** your session list to find every conversation on a given topic.
* **Build metrics** in Reports that count and trend tagged sessions over time (for example, the share of sessions that involved a pricing question).&#x20;

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

## Pre-defined vs auto-generated

There are two ways an agent can end up with tags:

* **Pre-defined tags** — the tags _you_ define on this page, each with a name and a description of when to apply it. When you've defined one or more pre-defined tags, the AI evaluates **only** those tags for new sessions, giving you a consistent, controlled vocabulary across every conversation.
* **Auto-generated tags** — when an agent has **no** pre-defined tags, Wayfound instead generates a few descriptive tags per session on its own to summarize each conversation. These are useful out of the box but vary from session to session.

You can also combine the two — see **Including auto-generated tags** below.

## Defining a pre-defined tag

On the **Tags** page, the **Pre-Defined Tags** section is where you build your tag set. Click **Add Pre-Defined Tag** to create one, then fill in:

* **Tag Name** — a short, uppercase label (e.g., `PRICING-QUESTION`). Names are automatically converted to uppercase and spaces become underscores. Use only letters, numbers, underscores, and hyphens; each name must be unique on the agent, and shorter names read best in the session list.
* **Description (when to apply this tag)** — a natural-language description telling the AI exactly when this tag should be applied. This is the most important field: the clearer and more specific it is, the more accurately the tag will be applied. Aim for roughly 10–500 characters. _Example:_ "Apply this tag when the user asks about pricing, costs, payment options, or billing information."
* **Active** — a toggle that controls whether the tag is currently evaluated. Turn it off to pause a tag without deleting it; inactive tags are skipped when new sessions are tagged.

Use the trash icon on a tag card to remove a tag entirely.

## Including auto-generated tags

Once you've added at least one pre-defined tag, an **Also include auto-generated tags** toggle appears at the top of the section. When enabled, Wayfound applies your matching pre-defined tags **and** adds a small number of AI-generated tags to capture anything your pre-defined set didn't cover. Leave it off to keep sessions strictly to your defined vocabulary; turn it on when you want broader coverage and are comfortable with some variation.

## Publishing your tags

Tags are part of your agent's configuration, so they follow the same draft-and-publish flow as the rest of Agent Settings. Edits you make here are saved to your **draft**; fields that differ from the published version are highlighted so you can see what's changed. **Publish the agent** to put your tags into effect for live sessions — only published tags are used to evaluate real traffic, while draft tags apply to test runs.

> Tags are applied to sessions **going forward**, as new sessions are processed. Changing your tags doesn't re-tag sessions that were already analyzed.

## Using your tags

Once sessions are being tagged, your tags show up in two places:

* **Session list** — tags appear as badges on each session, and the **Tags** filter lets you include sessions _with_ selected tags or exclude sessions that carry them, so you can zero in on a topic quickly.
* **Reports & Metrics** — metric expressions in a Report reference your tag names to count and trend tagged sessions. For example, a metric expression like `PRICING-QUESTION / TOTAL_SESSIONS * 100` reports the percentage of sessions that involved a pricing question. See the **Reports** documentation for how to build metrics from your tags.

