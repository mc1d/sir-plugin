# $SIR plugin for Claude Code

Frontier models below list price, billed to your $SIR balance, from inside Claude Code.

```sh
claude plugin marketplace add mc1d/sir-plugin
claude plugin install sir@sir
export SIR_BASE_URL=https://<your gateway>/v1
export SIR_API_KEY=sk-sir-...
claude
```

## What you get

| | |
|---|---|
| `sir_models` | Every model on the gateway, its lab and list price |
| `sir_ask` | Ask any model: second opinions from GPT, Gemini or DeepSeek, cheap bulk work on `sir-base` |
| `sir_balance`, `sir_usage` | What the key can spend, and 30 days of spend by model |
| `sir_referral` | Your referral link and commission |
| `sir_setup` | Config for Cursor, Codex, Cline, Aider, opencode, Claude Desktop and any OpenAI SDK |
| `sir_wallet_key` | Make a key by signing locally with a Solana keypair. No sign-up |
| `/sir:setup` | Point Claude Code itself at $SIR, so every request is billed there |
| `/sir:balance` | Balance at a glance |
| `/sir:second-opinion` | Have another lab's model review the current plan or diff |

## Run Claude Code on $SIR

`/sir:setup` writes this for you, or set it yourself:

```sh
export ANTHROPIC_BASE_URL=https://<your gateway>      # no /v1: Claude Code adds /v1/messages
export ANTHROPIC_AUTH_TOKEN=$SIR_API_KEY
export ANTHROPIC_API_KEY=
claude
```

Claude model names map to $SIR models: opus to `sir-frontier-plus`, sonnet to `sir-frontier`, haiku to `sir-base`.

## Other tools

The same MCP server runs anywhere MCP does:

```json
{ "mcpServers": { "sir": { "command": "npx", "args": ["-y", "github:mc1d/sir-plugin"], "env": { "SIR_API_KEY": "sk-sir-...", "SIR_BASE_URL": "https://<your gateway>/v1" } } } }
```

`sir/server/sir-mcp.mjs` is a single bundled file with no dependencies, built from the $SIR monorepo. Needs Node 20 or newer.
