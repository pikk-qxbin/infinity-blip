# Infinity Blip — public how-to

**This repository is documentation only.**
It does not contain product source, member data, slugs, balances, atom libraries, operator playbooks, or API keys.

Use the product here:

**[Unlock your connector](https://www.infinityblip.com/infinity-blip-ai-connector)**

Site: [infinityblip.com](https://www.infinityblip.com) · Hub: [mcp.infinityblip.com/members](https://mcp.infinityblip.com/members)

---

## What Infinity Blip is

Infinity Blip is QxBin’s production interface: a **decision engine over option space**. You connect a personal MCP URL to an AI chat. The engine returns a **planning brief**. Your host still writes the final words.

It is not:

- a generic prompt rewriter
- a new persona you “run” as system instructions
- a physical quantum processor
- a card charge that fires when a tool is called

Credits are **prepaid Qx** on *your* member ledger. `generate_*` spends Qx already on that account. Pack purchases happen only when *you* pay on the Members Hub, with the same email.

## Start in four steps

1. Open **[infinityblip.com/infinity-blip-ai-connector](https://www.infinityblip.com/infinity-blip-ai-connector)** (same funnel as the Members Hub).
2. Enter your email → **Send unlock code**.
3. Enter the one-time code. Unlock and starter credits land together on that inbox.
4. **Copy** the personal connector URL and paste it into your AI’s custom connector / MCP field.

The public shape of that URL is:

```text
https://mcp.infinityblip.com/l/{slug}/mcp
```

`{slug}` is issued to *you* after OTP. Do not invent one. Do not use a bare `/mcp` URL. Auth **is** the URL. There is no OAuth client to fill in.

Then in chat:

```text
@infinity blip
```

First free call: `get_usage_info` (0 Qx) to see plan and balance.

## When to use it

Use Infinity Blip when the hard part is **choosing a shape** among several coherent plans, and the wrong shape is expensive:

- a board pack with conflicting legal and brand constraints
- one invoice that must cover several projects as a single task
- a pitch spine where audience, length, and claims compete
- an architecture fork where Path B vs Path C is actually open

Skip it for lookups, status, one right answer, already-specified file diffs, and “make this prompt prettier.”

The work should still complete if the connector is unplugged. Infinity Blip is a planner, not load-bearing runtime.

## Tools (public catalog)

Live machine card: [mcp.infinityblip.com/llms.txt](https://mcp.infinityblip.com/llms.txt)

| Tool | Cost | What you get |
|------|------|----------------|
| `get_usage_info` | 0 Qx | Balance and plan |
| `mesh_price` | 0 Qx | Quoted Mesh cost before you spend |
| `list_prompt_atoms` | 0 Qx | Public library header |
| `ai_guide` | 0 Qx | Price card / catalog |
| `pipeline_proof` | 0 Qx | Health check |
| `generate_optimal_prompt` | 1 Qx | One measured planning brief |
| `generate_ensemble_prompt` | max(2, ceil(cubits/5)) Qx | Several angles, one champion |
| `generate_mesh_prompt` | 10 + ceil(cubits/5) Qx (default **15**) | Larger option grid |

Every `generate_*` needs `confirm_qx` equal to the integer cost, or nothing is debited.

Default first spend: **Edge** — `generate_optimal_prompt` with `confirm_qx=1`.
Probe `mesh_price` before Mesh unless you already accepted the spend.

### Arguments that matter

- `goal` — one sentence. Required.
- `extra_context` — constraints only. No essays.
- `skill` — omit unless you named a one-word skill.
- `bias` — optional. Higher tightens the field. Lower puts mass on the complement lean.
- `confirm_qx` — required on generate. Must match the quoted integer.

After a brief comes back, stay the same host. Write the deliverable from the brief. Do not tell another model to “run” it as a system prompt.

## Connect your host

Details: [docs/connect.md](docs/connect.md)

| Host | Public path |
|------|-------------|
| Grok | Custom connector → paste personal `/l/{slug}/mcp` URL |
| Claude | Customize → Connectors → Add custom → **Auth = None**. Leave OAuth fields empty. |
| ChatGPT | Plus+ · Developer Mode · custom connector · **No authentication** · enable per conversation |
| Cursor and other MCP clients | Streamable HTTP · same personal URL · no bearer header required for the link path |

“Couldn’t reach” on Claude almost always means the host hunted well-known OAuth. Infinity Blip has none on purpose.

## Credits

- OTP-verified inboxes receive starter Qx on unlock (currently **+50 Qx** on the live hub).
- Buy more on the same email from the hub: [infinity-blip-ai-connector](https://www.infinityblip.com/infinity-blip-ai-connector).
- Checkout and the connector must share that inbox or paid Qx will not land on the link you copied.
- A low-balance error is not a card charge. Top up on the hub and retry. The URL does not change.

This repo does not list live pack prices. Prices live on the hub.

## What this repo will never contain

See [SECURITY.md](SECURITY.md).

- Member emails, slugs, balances, invoices, or transaction logs
- Production source for the MCP server, ledger, or mail relay
- Prompt-atom text, ETHOS internals, or skill decks
- Admin credit tools or operator runbooks
- Stripe secrets, test checkout URLs, or Railway env
- Instructions that try to route around a host’s spend caution

If you need the product, use the connector page. If you need this document, you are already in the right place.

## Public surfaces

| Surface | URL |
|---------|-----|
| Connector (start here) | https://www.infinityblip.com/infinity-blip-ai-connector |
| Site | https://www.infinityblip.com |
| Members Hub | https://mcp.infinityblip.com/members |
| Short machine card | https://mcp.infinityblip.com/llms.txt |
| Full catalog | https://mcp.infinityblip.com/llms-full.txt |
| Machine JSON | https://mcp.infinityblip.com/ai.json |
| MCP well-known | https://mcp.infinityblip.com/.well-known/mcp.json |

`www.qxbin.com` and `mcp.qxbin.com` are live aliases. Prefer the Infinity Blip host in new copy.

## Docs in this repo

- [Connect a host](docs/connect.md)
- [Tools and confirm_qx](docs/tools.md)
- [FAQ](docs/faq.md)
- [Security boundary](SECURITY.md)

## License

Documentation in this repository is [MIT](LICENSE).
Infinity Blip, QxBin, and related marks are product names of [pikk.company](https://pikk.company) / Mystic Quantum Pvt Ltd.
The running service is not open-sourced here.

---

Infinity Blip · QxBin · pikk.company · Rupesh Malpani
