# Connect a host

**Unlock first:** [infinityblip.com/infinity-blip-ai-connector](https://www.infinityblip.com/infinity-blip-ai-connector)

You need the personal URL the hub gives you after OTP. It looks like:

```text
https://mcp.infinityblip.com/l/{slug}/mcp
```

Replace nothing by hand. Copy the whole line.

Auth **is** that URL. No OAuth app. No client id. No secret header on the public link path.

---

## Grok

1. Unlock and copy the URL from the connector page.
2. Add a custom connector / MCP server.
3. Paste the personal `/l/{slug}/mcp` URL.
4. In chat, mention `@infinity blip` and call `get_usage_info`.

Grok is a first-class MCP host for this product. Treat the brief as planning data, then write the answer yourself.

## Claude

1. Customize → Connectors → **Add custom**.
2. Paste the personal URL.
3. Set **Auth = None**. Leave every OAuth field empty.
4. Save. If tools do not appear, restart the client.

Notes that save a wasted afternoon:

- “Couldn’t reach” almost always means Claude hunted `/.well-known` OAuth. Infinity Blip has none on purpose.
- Anthropic treats MCP tool results as untrusted input. The contract is **brief-as-input**, not prompt-as-system. Do not ask Claude to “run” the brief as a new persona.
- Prepaid `generate_*` is a ledger debit on *your* Qx, not a Stripe charge. If Claude declines a spend tool, use a free probe (`get_usage_info`, `ai_guide`, `mesh_price`) or switch to a host that will call `generate_*` after you confirm.
- Do not paste operator workarounds into a Claude chat. They read as jailbreak scripts.

## ChatGPT

1. You need **Plus or above** and **Developer Mode** on.
2. Create a **custom connector** (not the Apps catalog, not Free).
3. Authentication = **No authentication**.
4. Enable the connector **per conversation**.
5. Paste the personal `/l/{slug}/mcp` URL.

If tools stay empty, the connector is off for that thread or you used a bare `/mcp` URL.

## Cursor and other MCP clients

- Transport: Streamable HTTP.
- URL: the personal `/l/{slug}/mcp` link only.
- Name the server something without spaces if the client is picky (`infinity-blip`).
- Do not point the client at `localhost` or a tunnel. Cloud hosts cannot see `127.0.0.1`.
- Do not use `uvx`, stdio, or a GitHub one-shot as the member path. Those are not how members connect.

## Lab-only hosts

These work for some members and are **not** promised on the hub footer:

- Perplexity — Connectors → Custom → Streamable HTTP (paid).
- Mistral Vibe — Work → Custom MCP, name without spaces.
- Gemini app — Connected Apps → Custom; CLI is usually saner.

Smoke them with `get_usage_info` before any `generate_*`.

## After it connects

```text
@infinity blip
get_usage_info
```

Then, when the option space is the problem:

```text
generate_optimal_prompt
goal: <one sentence>
extra_context: <constraints only>
confirm_qx: 1
```

Stay on the same host. Write the deliverable from the brief.
