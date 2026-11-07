# MCP Server Design

Guidance for designing and auditing MCP servers that work well when driven by
agents. It focuses on the agent-facing surface: tools around user intent,
transport and authentication boundaries, client behavior, feedback, and audits.

## What it covers

[SKILL.md](SKILL.md) is the routing entrypoint. The references cover
[tool design](references/tool-design.md), [agent UX](references/agent-ux.md),
[security](references/security-threats.md), [client behavior](references/clients.md),
[observability](references/observability.md), and an
[audit checklist](references/audit-checklist.md). Additional references discuss
daemon architecture and gateway aggregation; examples contain concrete wire
shapes.

This is design guidance rather than a codebase architecture or SDK scaffolding
guide. Use the relevant MCP libraries for protocol mechanics and evaluate
opinionated recommendations in the context of your server. The checklist
separates general guidance from conditional patterns and stack-specific advice.

## Install

Clone the full repository into the agent skills directory:

```sh
mkdir -p ~/.agents/skills
git clone https://github.com/j2h4u/skill-mcp-server-design.git ~/.agents/skills/mcp-server-design
```

If the destination already exists, inspect it first; do not overwrite it. Reload
the skill according to your agent host's instructions.

## Update

```sh
git -C ~/.agents/skills/mcp-server-design pull --ff-only
```

## Use

Ask an agent to design or audit an MCP server, or invoke the skill explicitly:

```text
$mcp-server-design Review this server's tools for agent usability and safety.
```

The skill was originally developed inside
[oh-my-claude-plugins](https://github.com/j2h4u/oh-my-claude-plugins) and is
now maintained separately.

## License

[PolyForm Noncommercial 1.0.0](LICENSE.md) permits use under its stated terms.
For commercial use, request written permission from the copyright holder.
