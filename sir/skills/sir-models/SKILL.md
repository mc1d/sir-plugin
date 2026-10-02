---
name: sir-models
description: Use when the user wants another AI model's answer, a cross-check from a different lab (GPT, Gemini, DeepSeek), cheap bulk text work, or anything about their $SIR balance, usage, models or referral link.
---

The `sir` MCP server connects to the user's $SIR gateway. Everything it runs is billed to their $SIR balance (free daily allowance first, then SIRC), so keep prompts tight and set `max_tokens`.

Tools:
- `sir_models`: model ids, labs and list prices. Check it before picking a model; ids look like `sir-base`, `sir-frontier`, `sir-frontier-openai`.
- `sir_ask`: one prompt to one model. The model sees only what you send, so include the code and context it needs.
- `sir_balance`, `sir_usage`: what the key can spend, and 30 days of spend by model.
- `sir_referral`: the user's referral link and commission.
- `sir_setup`: exact config for Cursor, Codex, Cline, Aider, opencode, Claude Desktop or any OpenAI SDK.
- `sir_wallet_key`: makes an API key by signing locally with a Solana keypair file. The key spends that wallet's balance; don't echo it more than needed.

Good uses:
- Cross-check a risky change with a model from another lab (see `/sir:second-opinion`).
- Fan out cheap work (summaries, test data, renaming suggestions) to `sir-base`.
- Answer "how much have I spent" or "how much is left" without leaving the editor.

If a tool says SIR_BASE_URL or SIR_API_KEY is missing, tell the user to set them (the Developers page shows both) and restart Claude Code.
