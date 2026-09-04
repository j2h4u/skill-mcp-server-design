# skill-mcp-server-design

Design guidance for MCP servers that need to work well when driven by agents.

Use it to shape tool surfaces around user intent, choose transport and auth
boundaries, account for client behavior, design feedback loops, and audit
servers before they become hard to change.

## Use

Place this directory wherever your agent runtime loads skills from.

## Contents

`SKILL.md` is the routing entrypoint. `references/` holds the deeper material:
tool design, client compatibility, transport, security, observability, daemon
architecture, gateway aggregation, and audit checklists. `examples/` keeps
concrete wire shapes out of the main skill.

## History

Originally developed inside `oh-my-claude-plugins`; now maintained separately.
