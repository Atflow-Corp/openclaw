This directory contains per-agent `AGENTS.md` scaffolds for the OpenClaw multi-agent setup:

- `pm`
- `research`
- `planning`
- `design`
- `dev-lead`
- `dev-coder`
- `qa`

These files were created inside the repository because the configured absolute OpenClaw workspace paths in the current JSON point to `/Users/atflow/.openclaw/...`, which does not exist in the current environment.

If you want these to become the active OpenClaw workspaces, either:

1. copy each folder to the real OpenClaw workspace path you intend to use, or
2. update the OpenClaw config so each agent `workspace` points to these directories.

## ClawHub Skill Suggestions

The skills below were selected as optional external additions from the ClawHub ecosystem (`skills.sh`) to complement the role boundaries defined in each agent workspace.

Recommended mapping:

- `pm`
  - `project-manager`
    - install: `npx skills add https://github.com/404kidwiz/claude-supercode-skills --skill project-manager`
    - page: https://skills.sh/404kidwiz/claude-supercode-skills/project-manager
  - `pm-architect`
    - install: `npx skills add https://github.com/rysweet/amplihack --skill pm-architect`
    - page: https://skills.sh/rysweet/amplihack/pm-architect
- `research`
  - `deep-research`
    - install: `npx skills add https://github.com/199-biotechnologies/claude-deep-research-skill --skill deep-research`
    - page: https://skills.sh/199-biotechnologies/claude-deep-research-skill/deep-research
  - `research-codebase`
    - install: `npx skills add https://github.com/ferueda/agent-skills --skill research-codebase`
    - page: https://skills.sh/ferueda/agent-skills/research-codebase
- `design`
  - `frontend-ui-ux-engineer`
    - install: `npx skills add https://github.com/404kidwiz/claude-supercode-skills --skill frontend-ui-ux-engineer`
    - page: https://skills.sh/404kidwiz/claude-supercode-skills/frontend-ui-ux-engineer
  - `frontend-ui-ux`
    - install: `npx skills add https://github.com/code-yeongyu/oh-my-opencode --skill frontend-ui-ux`
    - page: https://skills.sh/code-yeongyu/oh-my-opencode/frontend-ui-ux
- `dev-lead`
  - `systematic-debugging`
    - install: `npx skills add https://github.com/vamseeachanta/workspace-hub --skill systematic-debugging`
    - page: https://skills.sh/vamseeachanta/workspace-hub/systematic-debugging
- `dev-coder`
  - `debugger`
    - install: `npx skills add https://github.com/rmyndharis/antigravity-skills --skill debugger`
    - page: https://skills.sh/rmyndharis/antigravity-skills/debugger
- `qa`
  - `qa-test-planner`
    - install: `npx skills add https://github.com/softaworks/agent-toolkit --skill qa-test-planner`
    - page: https://skills.sh/softaworks/agent-toolkit/qa-test-planner
  - `code-review`
    - install: `npx skills add https://github.com/rsmdt/the-startup --skill code-review`
    - page: https://skills.sh/rsmdt/the-startup/code-review
  - `e2e-testing`
    - install: `npx skills add https://github.com/hieutrtr/ai1-skills --skill e2e-testing`
    - page: https://skills.sh/hieutrtr/ai1-skills/e2e-testing

Notes:

- `planning` is intentionally left without an external ClawHub dependency for now. The built-in local planning workflow is already a good fit, and the external candidates found were either too broad or overlapped heavily with `pm`.
- These are optional supplements, not replacements for the workspace-level `AGENTS.md` role definitions.
- Prefer adding only 1-2 skills per agent at first. Too many skills tend to blur role boundaries.
- For this setup, the highest-value starting point is:
  - `pm`: `project-manager` or `pm-architect`
  - `research`: `deep-research`
  - `design`: `frontend-ui-ux-engineer`
  - `qa`: `qa-test-planner` and `code-review`
