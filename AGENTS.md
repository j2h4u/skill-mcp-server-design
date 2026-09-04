# AGENTS.md

Keep the repository root installable as a skill directory: `SKILL.md`,
`references/`, and `examples/` should remain at the top level. Do not introduce
marketplace plugin packaging unless explicitly requested.

When changing the skill, keep `SKILL.md` as the routing and always-loaded
entrypoint. Put detailed or conditional material in `references/` and concrete
usage samples in `examples/`.

Before handing off changes, verify Markdown links and `SKILL.md` frontmatter.
