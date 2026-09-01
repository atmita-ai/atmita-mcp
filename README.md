# Atmita MCP

Connect any AI to your [Atmita](https://www.atmita.com) personal agent over MCP. One connection gives the AI you already use a line to your agent — and through it, every account your agent is connected to: WhatsApp, email, calendar, and 100+ tools.

**Endpoint (remote, streamable HTTP):**

```
https://webhook-handler-2vwnts7qcq-uc.a.run.app/mcp
```

Auth is OAuth 2.1 (dynamic client registration + PKCE) — paste the URL, sign in with your Atmita account (Google, Apple, or email), approve, done. New to Atmita? The sign-in page creates your account on the spot.

## Tools

| Tool | What it does |
|---|---|
| `send_message` | Send a message to your Atmita agent. It runs a full agent turn in the background — the reply also lands in your Atmita feed (or silently, your caller's choice). |
| `get_result` | Poll the agent's reply for an earlier `send_message`. |

## Connect

- **claude.ai** — Settings → Connectors → Add custom connector → paste the URL.
- **Claude Code** — `claude mcp add --transport http -s user atmita https://webhook-handler-2vwnts7qcq-uc.a.run.app/mcp`, then `/mcp` → authenticate.
- **ChatGPT** — Settings → Apps → Advanced → Developer mode → add connector with the URL.
- **Cursor** — [Add to Cursor](https://cursor.com/en/install-mcp?name=atmita&config=eyJ1cmwiOiJodHRwczovL3dlYmhvb2staGFuZGxlci0ydndudHM3cWNxLXVjLmEucnVuLmFwcC9tY3AifQ%3D%3D), or add `{"atmita": {"url": "https://webhook-handler-2vwnts7qcq-uc.a.run.app/mcp"}}` to `mcp.json`.
- **Zapier** — add "MCP Client by Zapier" to a Zap, paste the URL, mark it as requiring OAuth.

## Spec

Stateless streamable HTTP per MCP spec 2025-11-25. OAuth discovery: [`/.well-known/oauth-protected-resource/mcp`](https://webhook-handler-2vwnts7qcq-uc.a.run.app/.well-known/oauth-protected-resource/mcp). The server implementation lives in Atmita's main (private) codebase; this repo is its public front door.
