---
name: codex-budget-model-router
description: >-
  Route Codex parent and subagent work to the most token-efficient and cost-efficient
  capable model for each task. Keep the parent on GPT-6 Luna / max, routine
  subagent tasks on GPT-6.1 Terra / low, and computer-use subagents on GPT-6
  Luna / max.
---

# Codex Budget Model Router

Independent community project. Not affiliated with or endorsed by OpenAI.

Use this skill when Codex work can benefit from scoped subagents. The parent/main agent stays on GPT-6 Luna / max. The model picker routes subagents only; it never changes the parent. Any other model or provider must run in a scoped subagent.

The parent owns the user's goal, task split, shared files, integration, verification, and acceptance. It handles routine work from small to high when delegation does not improve delivery. It gathers child results and verifies them before accepting the outcome.

## Cost-first routing

Choose the least usage-expensive model that still meets the task's quality, tool, and risk needs. Do not choose the strongest model by default. Count the parent's context, child work, tool calls, retries, repair, review, integration, and time when judging efficiency.

Real Codex usage testing found GPT-6 Luna / max significantly more usage-expensive than GPT-6.1 Terra / low. Route routine subagent tasks from small through high to Terra / low. Keep Luna / max for the parent, computer-use subagents, and nonroutine work that needs independent high-assurance review or coordination.

## Model-to-task breakdown

| Work | Owner and model | Reason |
|---|---|---|
| Parent work, including routine tasks from small to high | Parent: GPT-6 Luna / max | Fixed parent route; the child picker never changes it. |
| Routine subagent tasks from small through high, including coding, research, audit, routine review, and verification | Subagent: GPT-6.1 Terra / low | Use the lowest-cost tested route that remains capable for routine work. |
| Computer-use subagent tasks | Computer-use-capable subagent: GPT-6 Luna / max | Use Luna / max for delegated computer interaction. Confirm the child has the required computer-use tools. |
| Nonroutine consequential independent review | Subagent: GPT-6 Luna / max | Use only when stronger independent assurance materially improves confidence. |
| Hard, complex, or high-risk implementation | Subagent: GPT-6.2 Sol / medium | Use when the task needs stronger reasoning or integration. |
| Ultra-complex implementation estimated under 10 minutes | Subagent: GPT-6.2 Sol / high | Use medium when duration is 10 minutes or more, or unknown. |
| Coordination for at least three dependent scopes | Optional subagent: GPT-6 Luna / max | Use only when dedicated coordination materially helps. |
| Astra | Child by current-task user request only | Never select automatically. |

A GPT-6 Luna / max child may be used for computer work only when the selected child also has the required tools. Select a runtime-supported role, set `model` and `reasoning_effort` explicitly, and verify the observed child route. A role name alone does not prove the model or effort.

This skill cannot change a running parent's model. Configure the host to start the parent on Luna / max. If current runtime metadata shows another route, report the mismatch and do not claim the parent route changed.

## Plus usage

ChatGPT Plus is currently listed at $20/month and includes Codex usage subject to plan and account limits. This router helps Plus users make that allowance last. Its working assumption is that routine assignments often gain little practical value from higher model or effort settings, while those settings can consume substantially more usage. Start with the lowest-cost tested route that remains capable, then escalate when complexity, risk, or observed results warrant it. Treat this as a budget heuristic, not a guarantee. API token prices are separate from subscription usage and do not predict Plus usage. Verify current pricing, model availability, and usage limits because they can change. See [ChatGPT Plus](https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus), [Using Codex with your ChatGPT plan](https://help.openai.com/en/articles/11369540-using-codex-with-your-chatgpt-plan), and [Codex usage limits](https://help.openai.com/en/articles/20001625-understanding-chatgpt-and-codex-usage-limits).

## Dispatch and escalation

1. Keep simple work with the parent when delegation overhead exceeds the gain.
2. Route routine child work from small through high to GPT-6.1 Terra / low.
3. Route computer-use subagents to GPT-6 Luna / max and confirm they have the required tools.
4. Split only independent or clearly bounded work.
5. Give each child the task, context, allowed tools, exact write scope, success check, stop rule, and return format.
6. Use `fork_turns: "none"` when the child needs a different route from the parent.
7. Escalate only when evidence shows the routine Terra / low route is not enough. Use Sol / medium for hard, complex, or high-risk implementation. Use Sol / high only for ultra-complex work estimated under 10 minutes.
8. The parent collects child reports, integrates work, checks evidence, and owns final acceptance. Child completion is not final acceptance.
9. If the runtime cannot set or verify the requested child model, effort, or required tools, keep the work with the parent instead of guessing.

## Authority and availability

This skill selects model routes. It does not grant permission to edit shared files, send messages, spend money, publish, deploy, delete data, or access an account. Follow the user's existing authorization and real approval gates.

Model availability, picker controls, effort settings, and usage limits vary by client and plan. Use a supported route only when its actual model and effort can be verified.