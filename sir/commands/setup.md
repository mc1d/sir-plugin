---
description: Bill Claude Code to your $SIR balance instead of an Anthropic plan
argument-hint: "[project|user]"
---

Switch this Claude Code install to run on the $SIR gateway, so requests spend the user's free daily $SIR allowance first, then SIRC at their Core's discount.

1. Check that `SIR_BASE_URL` and `SIR_API_KEY` are set in the environment. If either is missing, tell the user where to get them (the Developers page on the $SIR site, or the `sir_wallet_key` tool to make a key from a local Solana keypair) and stop.
2. Call `sir_balance` to confirm the key works and show what it can spend.
3. Ask which scope to write, unless "$ARGUMENTS" already says: `project` writes `.claude/settings.local.json` in this repo (not committed), `user` writes `~/.claude/settings.json`.
4. Merge into that file's `env` object, keeping everything else in the file:
   - `ANTHROPIC_BASE_URL`: `SIR_BASE_URL` with any trailing `/v1` removed (Claude Code adds `/v1/messages` itself)
   - `ANTHROPIC_AUTH_TOKEN`: the value of `SIR_API_KEY`
   - `ANTHROPIC_API_KEY`: empty string
5. Tell the user to restart Claude Code, and to run `/logout` once first if they were signed in to an Anthropic account. Mention that Claude model names map to $SIR models: opus to sir-frontier-plus, sonnet to sir-frontier, haiku to sir-base.

Never print the full key back to the user. To undo, remove those three keys from the same file.
