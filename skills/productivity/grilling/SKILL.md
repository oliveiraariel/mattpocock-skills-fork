---
name: grilling
description: Grill the user relentlessly about a plan, decision, or idea. Use when the user wants to stress-test their thinking, or uses any 'grill' trigger phrases.
---

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask _now_ without guessing at answers you haven't heard yet. Ask a practical bounded batch from the **currently unblocked** frontier in one round: number each question and give your recommended answer. Prioritize material decisions and group independent questions when helpful. Do not flood the user with every possible question at once. Then wait for the user's answers before the next round.

Format a round like so:

```
❓ **Q1** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>

---

❓ **Q2** - **<question title>**: <question body, might be multiple paragraphs, including multiple choices>

➡️ <your recommended answer>
```

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. A question whose answer depends on another question still open in this round belongs to a _later_ round, not this one.

Finding _facts_ is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent to find it; don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report; ask the rest of the frontier now. The _decisions_ are the user's: put each to them and wait.

## Documentation-aware software interviews

When planning, changing or auditing software, inspect the project's existing specifications, decisions and documentation standard **before** building the decision tree. If available, use its artifact catalog and elicitation coverage matrix to derive questions from gaps in product outcomes, requirements, rules, workflows, quality attributes, data, security, architecture, interfaces, tests, deployment and maintenance. Do not assume a PRD or separate file is mandatory. Distinguish human decisions from discoverable facts.

For each material resolved answer, record or propose a durable decision entry with ID, authority, scope/baseline, affected artifact/requirement IDs, alternatives and rationale. Where permitted, update the canonical decision ledger/document; otherwise provide an explicit decision handoff. **Never claim the interview alone published a spec.** Open issues and implementation blockers remain visible.

The session is done when the applicable frontier is empty: material branches explored, nothing silently assumed, and decisions are available to downstream documentation/specification. Do not act on unresolved decisions until the user confirms shared understanding.
