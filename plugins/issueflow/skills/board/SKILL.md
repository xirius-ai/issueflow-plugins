---
name: board
description: Show the user's IssueFlow board - what's running, what's stuck, and what's waiting on them. Use when the user asks about IssueFlow status, their issues or runs, "what's waiting on me", "what's going on", or "why is this issue stuck".
---

# The IssueFlow board

IssueFlow runs GitHub issues through a workflow of AI agent stages (design, implementation, review, merge...). People decide at gates and answer agents' questions. Use the `issueflow` MCP tools to show the user where things stand.

## Steps

1. **Orient.** If you haven't yet in this conversation, call `operator_start`. It says whether the account is set up and which solutions exist. If setup isn't finished, help with that first (see the `get-started` skill).
2. **One call for the overview.** Call `operator_board_digest`, for one solution when the user names it, otherwise for all. It returns what needs attention.
3. **What's waiting on the user.** Call `operator_waiting_on_human`. These are the items only a person can move: gate approvals, agents' questions, hand-offs.
4. **Drill in only when asked.** For "why is #123 stuck?", find the issue with `operator_list_issues`, then read `operator_issue_hold` (its live hold and the choices it accepts) and, if needed, `operator_issue_detail` (its runs and event trail).

## How to answer

- Lead with what needs the user, most urgent first. Then what's running. Then anything failing or stalled.
- Name issues by their repository and number (for example `acme/web#123`) and title, never by internal ids.
- Explain a hold in plain words: who is waiting on what, and what each choice would do.
- This skill only reads. To act on an item, use the `respond` skill, which confirms with the user first.
