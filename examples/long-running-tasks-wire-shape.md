# Worked example — Tasks wire shape

> Load when implementing the spec-extension long-running pattern. Tasks moved into
> the formal MCP extensions framework in 2026-07-28, so declaration shape is
> revision- and SDK-sensitive. Use the roll-your-own pattern (bottom of this file,
> also in [tool-design.md §Fallback](../references/tool-design.md#fallback--roll-your-own-async-handle))
> as the default for mixed or unverified clients; verify SDK support and
> [clients.md cross-client matrix](../references/clients.md#cross-client-capability-matrix)
> before shipping a Tasks-only flow.
>
> Decision context — when to reach for this vs. blocking vs. roll-your-own: [tool-design.md §Long-Running Operations](../references/tool-design.md#long-running-operations).

## 1. Declare Tasks support for your target revision

In older drafts this was a top-level `tasks` capability during `initialize`.
In 2026-07-28, Tasks are an opt-in extension and may be exposed through the
current SDK's extension API. Treat this JSON as illustrative only; verify the
SDK/runtime contract before shipping:

```jsonc
{
  "capabilities": {
    "tools": {},
    "tasks": { "requests": { "tools/call": true } }
  }
}
```

## 2. Declare per-tool intent when your SDK supports it

```jsonc
{
  "name": "deep_research",
  "description": "...",
  "execution": { "taskSupport": "optional" }  // "forbidden" | "optional" | "required"
}
```

When this field exists in your target revision, `"optional"` is the compatible
choice: clients without Tasks support invoke the tool synchronously or through
your roll-your-own fallback; clients with Tasks support may augment. **Do not
ship a required/spec-only path until the [clients.md matrix](../references/clients.md#cross-client-capability-matrix)
confirms every target client supports Tasks.**

| Value | Meaning |
|-------|---------|
| `forbidden` | Default. Tool is invoked synchronously; no task augmentation. |
| `optional` | Client may choose to augment with a task or call synchronously. |
| `required` | Client must augment with a task — synchronous call is rejected. |

## 3. Wire shape when the client augments

```jsonc
// Client → server
{"method":"tools/call","params":{"name":"deep_research","arguments":{...},"task":{"ttl":600000}}}
// Server → client (immediate)
{"result":{"taskId":"...","status":"working","createdAt":"...","ttl":600000,"pollInterval":2000}}
// Client polls
{"method":"tasks/get","params":{"taskId":"..."}}
// Terminal: working | input_required | completed | failed | cancelled
{"method":"tasks/result","params":{"taskId":"..."}}  // returns the original CallToolResult
{"method":"tasks/cancel","params":{"taskId":"..."}}  // optional
```

## Server-side invariants

- The receiver generates the task ID and may shorten the requested `ttl`.
- Clients poll. `notifications/tasks/status` is optional — requestors must not rely on it.
- Bind tasks to the authenticated principal or explicit domain handle; use high-entropy IDs.

## Roll-your-own fallback (use today)

Two ordinary tools, no spec feature:

1. Submit tool returns immediately with a domain `id` and `status: "working"`.
2. A separate polling tool (`get_task_status`, `check_job_result`) takes the `id` and returns current state.
3. Final state returns the actual result or error.

Same invariant: the first tool never blocks; it only enqueues work and returns a handle. The pattern leaks polling cadence into prompt engineering and depends on the agent remembering to call the status tool — switch to the spec extension above once your target clients support it.
