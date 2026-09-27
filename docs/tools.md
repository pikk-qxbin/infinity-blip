# Tools and confirm_qx

Live source of truth for names and prices:

- [llms.txt](https://mcp.infinityblip.com/llms.txt)
- [llms-full.txt](https://mcp.infinityblip.com/llms-full.txt)
- [ai.json](https://mcp.infinityblip.com/ai.json)

This page is a human copy of the public contract. It is not the atom library.

## Free (0 Qx)

Call these first on a new host.

| Tool | Why |
|------|-----|
| `get_usage_info` | Read balance and plan. No debit. |
| `mesh_price` | Quote Mesh cost before you accept it. |
| `list_prompt_atoms` | Library header only. Not the atom text. |
| `ai_guide` | Price card / catalog. Not a host-behavior playbook. |
| `pipeline_proof` | Health check. |

## Prepaid debit

`generate_*` spends Qx already on **this connected member account**. It does not open Stripe, does not charge a card, and does not buy a pack.

| Tool | Typical cost | Use when |
|------|----------------|----------|
| `generate_optimal_prompt` | **1 Qx** | One measured brief. Default first spend. |
| `generate_ensemble_prompt` | max(2, ceil(cubits/5)) Qx | You need distinct angles, not a tighter rewrite. |
| `generate_mesh_prompt` | 10 + ceil(cubits/5) Qx, default **15** | Hard decision space. Probe `mesh_price` first. |

### confirm_qx

Every `generate_*` call must pass `confirm_qx` equal to the **integer cost**.

- Edge: `confirm_qx=1`
- Ensemble: `confirm_qx=<quoted integer>`
- Mesh: `confirm_qx=<quoted integer>` (15 on the default grid)

If `confirm_qx` is missing or does not match, the server does not debit.

## How to phrase a call

Keep `goal` to one sentence. Keep `extra_context` to constraints.

```text
goal: Draft one commercial invoice that covers three live projects as a single task.
extra_context: A4; same client; itemize by project; INR; no new legal opinions.
confirm_qx: 1
```

Do not put essays in `extra_context`. Do not set `skill` unless you named a one-word skill. Do not reuse a prior `bias` silently.

## What comes back

A **planning brief** (data). The host should:

1. Stay itself.
2. Quote or paraphrase the brief.
3. Write *your* deliverable.

The host should not:

- announce that it is “running a prompt”
- hand the brief to another model as a system prompt
- treat Infinity Blip as a rewriter for a sentence that already has one right shape

## Modes that are not spend permits

Some hosts expose `get_blip_mode` / chat-force preferences. `always_on` is a preference, not permission to debit. Do not turn it on unless the human asked, and then only with an explicit confirm when the tool requires one.

Admin credit tools are owner-only and are not documented here.
