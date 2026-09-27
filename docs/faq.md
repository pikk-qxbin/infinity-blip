# FAQ

## Where do I start?

[https://www.infinityblip.com/infinity-blip-ai-connector](https://www.infinityblip.com/infinity-blip-ai-connector)

Same funnel as [mcp.infinityblip.com/members](https://mcp.infinityblip.com/members).

## I did not get the email code

Check spam and promotions. Wait a minute. Request a new code. Confirm the address is typed correctly. Codes last about 15 minutes on the live hub.

## What does starter credit mean?

OTP-verified inboxes receive starter Qx on unlock. The live hub copy is **+50 Qx** in the same step as the connector. Probe / test addresses are not credited.

## Can I share my URL?

No. The personal `/l/{slug}/mcp` link *is* the credential. Anyone with it can spend *your* prepaid Qx. Treat it like a password.

## Why does Claude say it could not reach the server?

It hunted OAuth well-known URLs. Set **Auth = None**. Do not fill client id / secret / callback.

## Why does a host refuse generate_*?

Some hosts treat metered MCP tools as unverifiable spend. That is the host’s judgment. Product-side facts:

- debit is prepaid Qx on this member ledger
- default Mesh is 15 Qx, not a 500 Qx pack
- packs are bought only on the hub by a human

Use free tools first. Confirm `confirm_qx`. Do not paste a workaround playbook into that chat.

## I bought a pack and the balance did not move

Checkout email and connector email must match. Unlock first so paid Qx can land on that inbox. Then `get_usage_info`.

## Tools list is empty

- You used a bare `/mcp` instead of `/l/{slug}/mcp`
- The connector is off for this conversation
- The client still expects OAuth
- You pointed at localhost

Fix the URL. Restart the client. Call `@infinity blip` once.

## Is this open source?

This repository is the public how-to. The running service, ledger, and prompt library are not published here. See [SECURITY.md](../SECURITY.md).

## Does Infinity Blip “solves hallucinations”?

No. It is a measured planner over option space. The host still owns the final words. Do not claim a solved-hallucination product.

## Failure table

| What you see | What it is | What you do |
|--------------|------------|-------------|
| Couldn’t reach / OAuth 404 | Host hunted well-known | Auth = None. No client id. |
| Tools listed, `generate_*` refused | Host spend caution or per-chat toggle | Free probe first. Same slug on Grok or Cursor. |
| 500 Qx / pack scare | Hub pack conflated with Mesh | Default Mesh is 15 prepaid Qx. |
| Empty tools | Bare `/mcp` or tools off | Personal `/l/{slug}/mcp` only. |
| localhost rejected | Cloud host cannot see 127.0.0.1 | Public personal URL. No member tunnels. |
| `uvx` / stdio in the chat | Old operator path leaked | Delete. Public path is the slug URL. |
