# AGENTS.md

This repository contains the `mcp-server-design` skill.

Keep the repository root installable as a skill directory: `SKILL.md`,
`references/`, and `examples/` should remain at the top level. Do not introduce
marketplace plugin packaging unless explicitly requested.

When changing the skill, keep `SKILL.md` as the routing and always-loaded
entrypoint. Put detailed or conditional material in `references/` and concrete
usage samples in `examples/`.

Before handing off changes, verify that all Markdown links resolve within the
repository and that `SKILL.md` frontmatter remains valid YAML.
