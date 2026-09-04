# MCP Server Design

Design guidance for MCP servers that need to work well when driven by agents.

This is not a codebase-architecture or SDK scaffolding guide. Use the standard
MCP libraries for protocol mechanics; use this skill to shape the server's
agent-facing surface: tools around user intent, transport and auth boundaries,
client behavior, feedback loops, and audits before the surface becomes hard to
change.

## Use

Give your agent this repository URL and ask it to install the skill:
`https://github.com/j2h4u/skill-mcp-server-design`.

## Contents

`SKILL.md` is the routing entrypoint. `references/` holds the deeper material:
tool design, client compatibility, transport, security, observability, daemon
architecture, gateway aggregation, and audit checklists. `examples/` keeps
concrete wire shapes out of the main skill.

## History

Originally developed inside
[`oh-my-claude-plugins`](https://github.com/j2h4u/oh-my-claude-plugins);
now maintained separately.
