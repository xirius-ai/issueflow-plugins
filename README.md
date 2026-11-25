# IssueFlow plugins

Plugins and connectors that bring [IssueFlow](https://www.issueflow.cloud) into the AI chat tools you already use. IssueFlow is workflow orchestration for AI coding agents.

They all connect to the IssueFlow MCP server:

```
https://api.issueflow.cloud/mcp
```

From your chat agent you can read your board, see what's waiting on you, understand why an issue is held, and answer holds. Before you sign in, the agent can read the public documentation.

## Status

| Client | Status |
|---|---|
| Any MCP client (Claude, ChatGPT, VS Code, Cursor…) | Available: add the URL above as a remote MCP server |
| MCP Registry | Listed as `io.github.xirius-ai/issueflow` |
| Claude Code plugin | Available: see below |

## Claude Code plugin

The `issueflow` plugin connects Claude Code to IssueFlow and adds three skills: **board** (what's running and what's waiting on you), **respond** (answer a hold or gate, after you confirm) and **get-started** (setup and "how do I" questions, answered from the docs).

```
/plugin install issueflow --marketplace xirius-ai/issueflow-plugins
```

The first time Claude uses IssueFlow, it opens a browser window to sign you in with GitHub.

## Help

- Documentation: <https://portal.issueflow.cloud/docs>
- Questions and ideas: [IssueFlow Community discussions](https://github.com/xirius-ai/issueflow-community/discussions)
- Security issues: email info@xirius.com with "Security" in the subject
