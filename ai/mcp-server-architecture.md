# Why Model Context Protocol Beats Custom REST Endpoints for AI

## The Tooling Bottleneck

Building custom REST endpoints for every Claude or Cursor capability is unscalable.

- MCP (Model Context Protocol) standardizes how AI agents discover tools, inspect schemas, and query databases.
- By exposing our internal NestJS services as an MCP server with Server-Sent Events (SSE), any AI model can safely inspect our schemas without custom integration code.

## Production Security for MCP

Never give an MCP server raw DB write access:

- Enforce strict JSON Schema validation via Zod on every tool call payload.
- All mutating actions (refunds, deletes) require explicit human-in-the-loop confirmation tokens before execution.
