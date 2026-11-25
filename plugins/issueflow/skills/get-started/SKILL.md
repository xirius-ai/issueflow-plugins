---
name: get-started
description: Help the user learn, set up or configure IssueFlow - what it is, connecting GitHub, installing a worker, designing a workflow, or any "how do I" question about IssueFlow. Works before the user has signed in.
---

# Getting started with IssueFlow

IssueFlow runs GitHub issues through a delivery workflow the user designs, using the AI coding agents they already use, on their own machines, with human approval where they choose. Its documentation is served by the `issueflow` MCP server, readable before sign-in.

## Answer from the docs, not from memory

1. For a "how do I" or "what is" question, call `issueflow_list_docs` and read the relevant page with `issueflow_get_doc`. The server's prompts (also readable with `issueflow_get_guide`) carry step-by-step guides.
2. Quote the steps that apply, and link the public page under `https://portal.issueflow.cloud/docs` when one exists.
3. If the docs don't cover it, say so. Don't guess at configuration keys. `issueflow_config_keys` lists what a config file accepts, and `issueflow_validate_config` checks a proposed configuration against the engine itself.

## Setting up an account

1. Call `operator_start`. It reports setup progress step by step, and what to do next.
2. Walk the user through the next unfinished step only, then call `operator_start` again to confirm it moved.
3. Signing up, connecting GitHub and installing a worker happen in the portal (`https://portal.issueflow.cloud`) and on the user's own machine. Give the user the steps; you can't do them for them.

## Getting help

The community forum is at https://github.com/xirius-ai/issueflow-community/discussions. For account or billing problems, the user can email info@xirius.com.
