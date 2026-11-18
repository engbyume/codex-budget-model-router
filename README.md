# Progressive Codex Model Router

A standalone Codex skill for assigning subagents the least costly model and effort that meet each task's quality and risk needs.

The parent agent stays on GPT-6.1 Terra / low (Terra Light) and handles routine low-to-medium coding directly. The model picker applies only to subagents; all other model routes are child-only. Configure the host to start the parent on Terra / low. The parent gathers child work, then integrates and verifies the result.

The full model-to-task breakdown, Plus plan context, and delegation guidance are in [SKILL.md](SKILL.md).

## Install

Copy this repository into a folder named `progressive-codex-model-router` in your Codex skills directory. Then invoke the skill by name in Codex.

This skill contains instructions only. It has no scripts or runtime dependencies.

## License

MIT. See [LICENSE](LICENSE).
