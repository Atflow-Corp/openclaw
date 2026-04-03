Git operating policy for the OpenClaw multi-agent setup.

## Identity and auth

- GitHub network auth is handled by the `atflow` user via SSH.
- Use SSH remotes by default.
- Keep global `user.email` unchanged.
- Override only `user.name` per agent when creating commits.

Recommended commit author names:

- `main` -> `OpenClaw Main`
- `pm` -> `OpenClaw PM`
- `research` -> `OpenClaw Research`
- `planning` -> `OpenClaw Planning`
- `design` -> `OpenClaw Design`
- `dev-lead` -> `OpenClaw Dev Lead`
- `dev-coder` -> `OpenClaw Dev Coder`
- `qa` -> `OpenClaw QA`

Example:

```bash
git -C /path/to/repo -c user.name="OpenClaw Dev Coder" commit -m "Implement feature"
```

## Default GitHub resolution

- If the user provides a full repository URL, use it as-is.
- If the user provides only a repository name, resolve it under the `Atflow-Corp` GitHub organization.
- Default SSH remote format:

```text
git@github.com:Atflow-Corp/<repo-name>.git
```

Examples:

- create repo name `vacation-bot` -> `Atflow-Corp/vacation-bot`
- clone repo name `vacation-bot` -> `git@github.com:Atflow-Corp/vacation-bot.git`

## Local path conventions

- Shared clone root:

```text
/Users/atflow/repos/<repo-name>
```

- Agent worktree root for parallel work:

```text
/Users/atflow/worktrees/<repo-name>/<agent-id>
```

Examples:

- main clone: `/Users/atflow/repos/vacation-bot`
- dev-coder worktree: `/Users/atflow/worktrees/vacation-bot/dev-coder`
- qa worktree: `/Users/atflow/worktrees/vacation-bot/qa`

## Workflow rules

- `pm` may initialize a new repository or clone an existing one.
- `pm` records the resolved repository path in `projects.yaml`.
- The official shared outputs of `pm`, `research`, `planning`, `design`, `dev-lead`, and `qa` should be committed into the project repository as Markdown files under `docs/`.
- Agent workspaces are for temporary notes and local context, not the primary long-term source of truth.
- `dev-lead`, `dev-coder`, and `qa` should work in the product repo or dedicated worktrees.
- For parallel implementation or verification, prefer Git worktrees over sharing the same checkout.
- Avoid multiple agents committing into the same checkout concurrently.

## Documentation policy

- Use the repository as the shared source of truth between agents.
- Store formal outputs under:

```text
docs/pm
docs/research
docs/planning
docs/design
docs/dev
docs/qa
```

- `planning`, `design`, `research`, and `qa` should generally create or update Markdown documents in the repository rather than leaving final outputs only in agent workspaces.
- `docs/dev` is for engineering execution artifacts such as architecture notes, implementation plans, and handoff documents.

## Platform standard

- Default project stack:
  - backend: Django
  - frontend: Django templates
  - local db: SQLite
  - test db: SQLite
  - production db: PostgreSQL
  - infrastructure: AWS
- Project-specific deviations should be captured as overrides in `projects.yaml`.

## Repo creation and clone policy

- Create:
  - if only repo name is given, create under `Atflow-Corp`
  - local clone path should default to `/Users/atflow/repos/<repo-name>`
- Clone:
  - if only repo name is given, clone `git@github.com:Atflow-Corp/<repo-name>.git`
  - local clone path should default to `/Users/atflow/repos/<repo-name>`
