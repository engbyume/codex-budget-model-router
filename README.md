# Codex Budget Model Router

A standalone community skill for budget-aware Codex parent and subagent routing. It is not affiliated with or endorsed by OpenAI.

## Built for ChatGPT Plus usage

OpenAI currently lists ChatGPT Plus at $20/month, with Codex usage subject to plan and account limits. This router aims to make that allowance last. Its working assumption is that routine assignments often gain little practical value from higher model or effort settings, while those settings can consume substantially more usage. Start with the lowest-cost tested route that remains capable, then escalate when complexity, risk, or observed results warrant it. Treat this as a budget heuristic, not a guarantee.

API token prices are separate from subscription usage and do not predict Plus usage. Check [ChatGPT Plus](https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus), [Using Codex with your ChatGPT plan](https://help.openai.com/en/articles/11369540-using-codex-with-your-chatgpt-plan), and [Codex usage limits](https://help.openai.com/en/articles/20001625-understanding-chatgpt-and-codex-usage-limits) for current details.

## Model and effort routes

| Work | Owner and model | Reason |
| --- | --- | --- |
| Parent work, including routine tasks from small to high | Parent: GPT-6 Luna / max | Fixed parent route. The child picker never changes it. |
| Routine subagent work from small through high, including coding, research, audits, routine review, and verification | Subagent: GPT-6.1 Terra / low | Lowest-cost tested route that remains capable for routine work. |
| Computer-use subagent work | Computer-use-capable subagent: GPT-6 Luna / max | Use only when the child has the required tools. |
| Nonroutine consequential independent review | Subagent: GPT-6 Luna / max | Use when stronger independent assurance materially improves confidence. |
| Hard, complex, or high-risk implementation | Subagent: GPT-6.2 Sol / medium | Use when the task needs stronger reasoning or integration. |
| Ultra-complex implementation estimated under 10 minutes | Subagent: GPT-6.2 Sol / high | Use medium when duration is 10 minutes or more, or unknown. |
| Coordination for at least three dependent scopes | Optional subagent: GPT-6 Luna / max | Use only when a dedicated coordinator materially helps. |
| Astra | Child by current-task user request only | Never select automatically. |

## Parent and subagents

The parent is the foreman. It stays on GPT-6 Luna / max, owns the task split and shared work, gathers child results, integrates and verifies them, and accepts the outcome. The model picker selects subagent routes only. A child never changes its parent's model.

## Install

Copy this repository into a folder named `codex-budget-model-router` in your Codex skills directory. Then invoke the skill by that name in Codex.

This skill contains instructions only. It has no scripts or runtime dependencies.

## License

MIT. See [LICENSE](LICENSE).
