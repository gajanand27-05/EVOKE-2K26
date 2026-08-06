# AGENTS.md

This document defines the working rules, workflow, and expectations for all agents (AI assistants) working in this repository. Read it fully before doing any work.

## Repository

- **GitHub repo:** https://github.com/gajanand27-05/inter-event-2026
- **Working directory:** `D:\inter-event-2026`

## The Rules (MUST FOLLOW)

1. **One task at a time.**
   - Every task is delivered as a prompt produced from ChatGPT (designed to be ~10x more efficient than a normal prompt).
   - Read the prompt **carefully** and completely.
   - Build a clear **plan** before touching code.
   - Implement the plan **step by step, one task at a time**.
   - Do **NOT** do all tasks at once.

2. **Report after every task completion.**
   - After each task is finished, write a **detailed report** so that the human and ChatGPT can understand exactly:
     - What was done.
     - Which files were changed/created.
     - How the solution works.
     - What was verified/tested (with actual output where relevant).
     - Anything blocked, pending, or needing a decision.

3. **Max 2 parallel agents.**
   - You may delegate work to agents (e.g. `explore`, `general`).
   - **Never** use more than **2** sub-agents at the same time.

4. **Commit & push protocol (IMPORTANT).**
   - **Commit:** always commit all changes locally after completing work (do NOT leave uncommitted work).
   - **Push approval:** never push without explicit approval, **except** the README file.
     - The **README.md** is pushed **directly** (no approval needed) so it is always visible on the repo.
     - For every other change: commit locally, then **ask the user for approval before pushing**.

5. **Git hygiene**
   - Meaningful, concise commit messages describing what changed.
   - Stay on the default branch.
   - Never commit secrets or credentials.

## Reporting template (use after each task)

```
## TASK REPORT

### Prompt summary
<what the prompt asked for>

### What was done
<step-by-step summary>

### Files changed
- `file/path` — what and why

### Verification
- <how it was verified / test command + output>

### Notes / blockers / decisions needed
<anything the human or ChatGPT must know>
```