---
name: codex-budget-model-router
description: >-
  Route Codex parent and subagent work by task difficulty. Use GPT-6 Luna / max
  for routine Easy and Medium tasks, GPT-6.1 Terra / low for routine Hard tasks,
  and GPT-6.2 Sol / medium for complex or high-risk implementation.
---

# Codex Budget Model Router

Independent community project. Not affiliated with or endorsed by OpenAI.

Use this skill before selecting a parent model or routing a subagent. Apply the same routine tiers to parent and subagent tasks. The parent model must be selected before the task starts; the subagent picker cannot change an already-running parent.

The parent owns the user's goal, task split, shared files, integration, verification, and acceptance. It handles routine work from small to high when delegation does not improve delivery. It gathers child results and verifies them before accepting the outcome.

## Cost-first routing

Choose the least usage-expensive model that still meets the task's quality, tool, and risk needs. Do not choose the strongest model by default. Count the parent's context, child work, tool calls, retries, repair, review, integration, and time when judging efficiency.

Use GPT-6 Luna / max for routine Easy and Medium tasks. Use the faster GPT-6.1 Terra / low route only for routine Hard tasks. Use GPT-6.2 Sol / medium for complex or high-risk implementation, including work previously assigned a higher Sol effort. Routine agentic work follows the same difficulty tiers; use Luna / max for computer use, nonroutine consequential review, and coordination when its capabilities materially help.

## Model-to-task breakdown

| Work | Owner and model | Reason |
|---|---|---|
| Parent or subagent: routine Easy and Medium tasks | GPT-6 Luna / max | Shared routine baseline for both roles. |
| Parent or subagent: routine Hard tasks | GPT-6.1 Terra / low | Faster Index task time; reserve for hard routine work where speed matters. |
| Computer-use subagent tasks | Computer-use-capable subagent: GPT-6 Luna / max | Use Luna / max for delegated computer interaction. Confirm the child has the required computer-use tools. |
| Nonroutine consequential independent review | Subagent: GPT-6 Luna / max | Use only when stronger independent assurance materially improves confidence. |
| Parent or subagent: complex or high-risk implementation | GPT-6.2 Sol / medium | Use when the task needs stronger reasoning or integration. |
| Coordination for at least three dependent scopes | Optional subagent: GPT-6 Luna / max | Use only when dedicated coordination materially helps. |
| Astra | Child by current-task user request only | Never select automatically. |

A GPT-6 Luna / max child may be used for computer work only when the selected child also has the required tools. Select a runtime-supported role, set `model` and `reasoning_effort` explicitly, and verify the observed child route. A role name alone does not prove the model or effort.

The router cannot change a running parent's model. Configure the host with the selected parent route before the task starts. If the host cannot set or verify that route, keep the actual route and report the limitation.

## Plus usage

This router targets ChatGPT Plus at $20/month and aims to keep included Codex use affordable. It routes routine Easy and Medium work to Luna / max, routine Hard work to the faster Terra / low route, and complex or high-risk implementation to Sol / medium. OpenAI sets plan usage separately from API pricing, and actual use varies by model, task, context, reasoning, speed, and tools. Verify current model availability and usage limits. See [ChatGPT Plus](https://help.openai.com/en/articles/6950777-what-is-chatgpt-plus), [Using Codex with your ChatGPT plan](https://help.openai.com/en/articles/11369540-using-codex-with-your-chatgpt-plan), and [Codex usage limits](https://help.openai.com/en/articles/20001625-understanding-chatgpt-and-codex-usage-limits).

## Dispatch and escalation

1. Keep simple work with the parent when delegation overhead exceeds the gain.
2. Use GPT-6 Luna / max for routine Easy and Medium work by the parent or a subagent.
3. Use GPT-6.1 Terra / low for routine Hard work by the parent or a subagent.
4. Split only independent or clearly bounded work.
5. Give each child the task, context, allowed tools, exact write scope, success check, stop rule, and return format.
6. Use `fork_turns: "none"` when the child needs a different route from the parent.
7. Use GPT-6.2 Sol / medium for complex or high-risk implementation, including ultra-complex work.
8. The parent collects child reports, integrates work, checks evidence, and owns final acceptance. Child completion is not final acceptance.
9. If the runtime cannot set or verify the requested child model, effort, or required tools, keep the work with the parent instead of guessing.

## Authority and availability

This skill selects model routes. It does not grant permission to edit shared files, send messages, spend money, publish, deploy, delete data, or access an account. Follow the user's existing authorization and real approval gates.

Model availability, picker controls, effort settings, and usage limits vary by client and plan. Use a supported route only when its actual model and effort can be verified.
