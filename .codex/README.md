# openDox Codex model routing

This project uses Codex-native Spec Kit skills. OpenSpec remains governance;
Spec Kit owns the existing feature artifacts and executable tasks.

| Role | Claude responsibility | Codex model | Reasoning |
|---|---|---|---|
| opendox-lead | Fable / lead Opus | gpt-6.2-astra | max |
| opendox-o | Opus [O] | gpt-6.2-astra | xhigh |
| opendox-s | Sonnet [S] | gpt-6.2-sol | high |
| opendox-h | Haiku [H] | gpt-6-luna | high |
| opendox-visual | visual/computer-use specialist | gpt-6.1-terra | high |

Sol is the implementation default. Terra is a visual specialist, not a general
replacement for Sonnet. Luna is the mechanical-task tier. There is no verified
GPT-6.2 Terra entry in the inspected catalog. No [H] task is admitted where the
code repository lacks a Governed invariants section.

Delegate by the existing tier; never downgrade security or contract work.
Keep one writer at a time in a feature worktree. Preserve each task's files and
verify scope. An unsuccessful [H] attempt may escalate to [S], then [O]; an [O]
failure returns to planning. Record requested and resolved model/effort when the
runtime exposes them; never label a requested model as proven execution.
If a model is unavailable, report it and explicitly escalate; no silent fallback.
Existing chats may retain their active model until the next launch/selection;
these files set project defaults, not proof of the current lead's model.

Feature 055 is owned by Opensoft-Tenant. Resume its existing S1b worktree and
set SPECIFY_FEATURE_DIRECTORY=specs/055-opendox-qa-hosted for each Spec Kit call;
do not overwrite shared selectors for other features. Use the existing spec,
plan and tasks, and the Codex speckit-analyze and speckit-implement skills.
All build/test/script commands run in py-bench at the repository's mounted path.
The desktop app and its integrated PowerShell remain Windows-native.

Current authorization: local S1b implementation and verification. Do not deploy,
merge, archive the feature, apply Terraform, mutate Keycloak/Key Vault/DNS, or
run operator commands from the runbook. Commands written into documentation are
examples until separately authorized for execution. Do not fabricate live evidence.

Sources checked 2026-11-20:
- https://learn.chatgpt.com/docs/agent-configuration/subagents
- https://learn.chatgpt.com/docs/models
- Shared OpenSpec/Speckit protocol, section Without subagents.
