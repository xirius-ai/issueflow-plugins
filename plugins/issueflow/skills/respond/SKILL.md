---
name: respond
description: Answer an IssueFlow hold for the user - approve or reject a gate, answer an agent's question, retry, pause or resume an issue. Use when the user wants to act on an IssueFlow issue that is waiting on them.
---

# Respond to an IssueFlow hold

When an issue is held, the workflow is waiting for a person. Each hold accepts only certain choices, and each choice changes the run, so always read before you act and confirm before you write.

## Steps

1. **Find the issue.** Use `operator_waiting_on_human`, or `operator_list_issues` when the user names an issue.
2. **Read its hold.** Call `operator_issue_hold`. It returns the reason for the hold, what the stage produced or asked, and the choices this run accepts right now, with what each one does.
3. **Explain and confirm.** Tell the user, in plain words, what is being asked and what each relevant choice would do. Recommend one when the evidence supports it. **Do not act until the user has chosen.**
4. **Act with the matching tool:**
   - A gate approval or rejection: `operator_gate_response` with the chosen verdict, and the user's reasoning as the comment.
   - An agent's question: `operator_answer` with the user's answer. The stage that asked runs again with it.
   - Run the stage again: `operator_retry`. Move the issue to another stage: `operator_restage_issue`.
   - Park or un-park: `operator_pause_issue` / `operator_resume_issue`.
5. **Report back.** Say what was recorded and what happens next. If the tool refused the action, say why and offer the choices the hold does accept.

## Care

- Cancel, restart and mark-complete are irreversible or discard work. Use them only when the user asks for exactly that, and say what will be lost first.
- Never invent an answer to an agent's question. If the user doesn't know, say so, and suggest pausing or asking a teammate.
- Put the user's words in comments, not yours. Comments are posted on the GitHub issue, where the team will read them.
