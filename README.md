# MCP Server Design

Design guidance for MCP servers that need to work well when driven by agents.

Use it to shape tool surfaces around user intent, choose transport and auth
boundaries, account for client behavior, design feedback loops, and audit
servers before they become hard to change.

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
