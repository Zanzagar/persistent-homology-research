# Project: Persistent Homology Research

Academic research on applying persistent homology (TDA) to the qualia convergence framework.

## Tech Stack

- No code — research and writing only
- Markdown for output documents

## Structure

```
docs/              # Source documents and output papers
.claude/rules/     # Auto-loaded behavior rules
```

## Project-Specific Patterns

- All source documents are in `docs/`
- Output documents go in `docs/` with descriptive names
- Academic tone, precise mathematical notation (LaTeX-style)

## Key Decisions & Constraints

- Research-only project — no TDD, no linting, no code
- Read ALL source documents before conducting external research
- Every claim must trace to source documents or cited references

## Gotchas & Watch-outs

- The term "qualia" is used metaphorically (operationalized via the LOGO test), not in the philosophical phenomenology sense
- Source docs include deprecated versions — only use the three current documents listed in `docs/00_DOCUMENT_INDEX.md`
- `.docx` files in `docs/` contain the persistent homology writeups (general research + personal research)

## Taskmaster Workflows

### Workflow Rules (MANDATORY)

1. **PRD first**: ALWAYS create a PRD before generating tasks. Never use `add-task` to build a task list from scratch — write a PRD in `.taskmaster/docs/`, then parse it.
2. **New tag per phase**: Each workflow phase gets its own tag (e.g., `writeup-ph`, `literature-review`). Never pollute the `master` tag with phase-specific work.
3. **Switch tags**: Always `task-master tags use <name>` before running set-status, show, or list — operations target the active tag.
4. **Expand after parse**: Always run `task-master expand --id=<id>` on complex tasks after parse-prd to generate actionable subtasks.
5. **Float task count**: Use `--num-tasks 0` with parse-prd to let the AI determine the right number of tasks. Don't hardcode counts.

### Commands

```bash
# List tasks (current tag)
task-master list                        # Default view
task-master list all                    # Include subtasks
task-master list --ready                # Only actionable tasks (deps satisfied)
task-master list --ready --blocking     # Highest-impact tasks to work on next

# Show / navigate
task-master show <id>                   # Task details
task-master next                        # Next recommended task

# Status updates (positional syntax)
task-master set-status <id> <status>    # e.g., set-status 3 done

# Task decomposition
task-master expand --id=<id>            # Break task into subtasks

# PRD -> tasks
task-master parse-prd --input=<file> --num-tasks=0

# Tag management
task-master tags use <tag-name>         # Switch active tag
```

## Research Workflow

### Daily Loop
1. Check task-master for next research task
2. Read source documents relevant to the task
3. Conduct external research if needed (WebSearch, WebFetch)
4. Write/revise output documents
5. Small, focused commits; update task status

## Current Focus

- [ ] ~5-page persistent homology writeup for professor meeting

## Relevant Slash Commands

| Command | Description |
|---------|-------------|
| `/research <topic>` | Structured research workflow |
| `/brainstorm <topic>` | Structured brainstorming |
| `/commit [message]` | Create conventional commit |
| `/tasks` | List Taskmaster tasks |
| `/task-status` | Update Taskmaster task status |
| `/checkpoint [label]` | Manual session state save |

## Source Documents

See `docs/00_DOCUMENT_INDEX.md` for the authoritative document index. Key files:

| Document | Purpose |
|----------|---------|
| `qualia_convergence_COMPLETE_VISION_v5.md` | Full intellectual vision (north star) |
| `qualia_convergence_IMPLEMENTATION_SPEC_v6.md` | Practical guide with phases and decision points |
| `qualia_convergence_ARCHITECTURE_DECISIONS_v1.md` | Reasoning behind design choices |
| `persistent_homology_writeup_general_research.docx` | General PH research writeup |
| `persistent_homology_writeup_my_research.docx` | Personal PH research writeup |
| `essence_thought_experiment.pdf` | Essence thought experiment |
