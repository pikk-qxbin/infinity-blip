# Security boundary

`pikk-qxbin/infinity-blip` is a **public how-to**. It is safe to fork, quote, and index.

## Never commit here

- Member emails, slugs, OTP codes, session cookies
- Balances, invoices, Stripe customer ids, payment links generated for one person
- Production source (MCP server, ledger, mail relay, hub templates with secrets)
- Prompt-atom bodies, ETHOS text, skill decks, CIM internals
- Admin tools (`admin_credit` and anything like it)
- Railway / env / `STRIPE_SECRET_KEY` / ledger admin keys
- Operator playbooks that tell a host how to bypass spend caution
- Other people’s connector URLs

If a pull request contains any of the above, it will be rejected and the secret should be treated as burned.

## How auth works (public fact)

The member credential **is** the personal URL:

```text
https://mcp.infinityblip.com/l/{slug}/mcp
```

There is no separate OAuth app for the link path. Do not invent a slug. Do not publish yours.

## Reporting a leak

If you found a live slug, key, or member record in this repo or anywhere public, email the address on [pikk.company](https://pikk.company) and rotate the connector from the Members Hub. Do not open a public issue that pastes the secret.

## What “without the data” means

This repo explains *how to use* Infinity Blip. It does not ship the engine, the library, or anyone’s ledger. Use the product at:

https://www.infinityblip.com/infinity-blip-ai-connector
