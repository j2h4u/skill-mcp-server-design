# skill-mcp-server-design

Design guidance for MCP servers: tool surfaces, transport choices, client behavior,
security boundaries, observability, and audit checks.

The skill itself is `mcp-server-design`. The repository name uses the `skill-*`
prefix so it is easy to find alongside other skill repositories.

## Local Install Example

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

- `SKILL.md` - entrypoint and core MCP server design guidance
- `references/` - detailed guidance for tool design, clients, transport,
  security, observability, daemon architecture, gateway aggregation, and audits
- `examples/` - concrete wire shapes and structured-output examples

## History

This skill was split out from
`j2h4u/oh-my-claude-plugins/meta/skills/mcp-server-design` into its own
repository so it can be maintained independently from the old plugin bundle.
