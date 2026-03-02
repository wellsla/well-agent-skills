---
name: orchestrating-agent-teams
description: Coordinate multiple Claude Code instances working together as a team, with shared tasks, inter-agent messaging, and centralized management. Use when exploring tasks in parallel, investigating bugs with competing hypotheses, or building features across different domains simultaneously.
---

# Orchestrating Agent Teams

## When to use this skill
- **Research and review**: Multiple teammates can investigate different aspects of a problem simultaneously, then share and challenge each other's findings.
- **New modules or features**: Teammates can each own a separate piece without stepping on each other.
- **Debugging with competing hypotheses**: Teammates test different theories in parallel and converge on the answer faster.
- **Cross-layer coordination**: Changes that span frontend, backend, and tests, each owned by a different teammate.

> **Note:** Agent teams add coordination overhead and use significantly more tokens. For sequential tasks, same-file edits, or work with many dependencies, a single session or subagents are better.

## Workflow

- [ ] **Enable Agent Teams**: Ensure `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS` is set to `1` in `settings.json` or environment.
- [ ] **Determine Display Mode**: Choose between "in-process" (default) or "split panes" (requires tmux/iTerm2). Set `teammateMode` in settings or use `--teammate-mode`.
- [ ] **Spawn the Team**: Ask the lead (current instance) to create an agent team. Provide a clear, natural language prompt describing the task and the desired team structure (e.g., "Create a team with 3 teammates: one on UX, one on architecture, one devil's advocate").
- [ ] **Assign Tasks / Claim Tasks**: Let the lead assign tasks explicitly or let teammates self-claim from a shared task list.
- [ ] **(Optional) Enforce Approvals**: Request plan approvals for teammates handling risky/complex components (e.g., "Require plan approval before they make any changes").
- [ ] **Coordinate / Intervene**: Monitor progress. Message teammates directly to steer them, or use Shift+Down in in-process mode to cycle through them. You can use the `message` to talk to one teammate, or `broadcast` to talk to all.
- [ ] **Synthesize & Clean up**: After tasks are complete, have the lead synthesize findings. Shut down teammates gracefully (`Ask the researcher teammate to shut down`), then finally tell the lead to `Clean up the team`.

## Instructions

### Enabling the Feature
To enable Agent Teams:
```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

### Display Modes
- **In-process**: All teammates run inside the main terminal. **Interacting**: Use Shift+Down to cycle through teammates, type to message, Enter to view session, Ctrl+T to toggle task list, Escape to interrupt turn.
- **Split panes (tmux/iTerm2)**: Each teammate has its own pane.

### Team Creation & Control

1. **Initial Prompt Example**: 
   > "Create an agent team to explore tracking TODO comments. One teammate on UX, one on technical architecture, one playing devil's advocate."
2. **Require Approvals**: 
   > "Spawn an architect teammate to refactor auth. Require plan approval before they make any changes."
3. **Shutdown & Cleanup**: 
   > "Ask the [Role] teammate to shut down."
   > "Wait for your teammates to complete their tasks."
   > "Clean up the team." *(Must be done by the lead to avoid corrupting shared task list/mailbox resources).*

### Architecture Mechanics
- **Lead / Caller**: Main session that spawns teammates and synthesizes results.
- **Task List**: Shared work items. Kept at `~/.claude/tasks/{team-name}/`.
- **Teammate Context**: Teammates load `CLAUDE.md`, MCPs, and skills from the project root. They *do not* get the lead's conversation history. Context must be passed via the spawn prompt.
- **File Locking**: Automatic. Make sure teammates are working on separate files to prevent concurrent access issues.

## Resources
- [Claude Code Agent Teams Documentation](https://code.claude.com/docs/llms.txt) (Reference material for advanced troubleshooting and hooks like `TeammateIdle` and `TaskCompleted`).
