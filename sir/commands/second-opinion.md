---
description: Get a second opinion on the current plan or diff from a model made by another lab
argument-hint: "[model id, e.g. sir-frontier-openai]"
---

Get an independent review from a different lab's model through $SIR.

1. Gather what needs reviewing: the plan you are about to carry out, or the current diff (`git diff` plus any new files), and the user's goal in one or two sentences.
2. Pick the model: "$ARGUMENTS" if given, otherwise call `sir_models` and choose one from a different lab than the one you are running on (prefer OpenAI, then Google, then DeepSeek).
3. Call `sir_ask` with a self-contained prompt: the goal, the plan or diff, and the request "List concrete problems: bugs, missed edge cases, security issues and simpler alternatives. Say 'no issues' if there are none. Be specific and brief." Set `max_tokens` to 1500.
4. Report back: the reviewer's points you agree with, the ones you don't and why, and what you will change. Do not apply changes until the user agrees, unless they asked you to.
