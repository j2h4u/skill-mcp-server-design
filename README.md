# skill-mcp-server-design

Design guidance for MCP servers that need to work well when driven by agents.

Use it to shape tool surfaces around user intent, choose transport and auth
boundaries, account for client behavior, design feedback loops, and audit
servers before they become hard to change.

## Install

```bash
mkdir -p ~/.agents/skills
rsync -a --delete ./ ~/.agents/skills/mcp-server-design/
```

For a remote host:

```bash
ssh hetz 'mkdir -p /home/j2h4u/.agents/skills/mcp-server-design'
rsync -a --delete ./ hetz:/home/j2h4u/.agents/skills/mcp-server-design/
```

## Contents

`SKILL.md` is the routing entrypoint. `references/` holds the deeper material:
tool design, client compatibility, transport, security, observability, daemon
architecture, gateway aggregation, and audit checklists. `examples/` keeps
concrete wire shapes out of the main skill.

## History

Originally developed inside `oh-my-claude-plugins`; now maintained separately.
