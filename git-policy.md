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
- `research`, `planning`, and `design` should usually write their own notes in agent workspaces, not directly into the product repo, unless the task explicitly asks for repo docs updates.
- `dev-lead`, `dev-coder`, and `qa` should work in the product repo or dedicated worktrees.
- For parallel implementation or verification, prefer Git worktrees over sharing the same checkout.
- Avoid multiple agents committing into the same checkout concurrently.

## Repo creation and clone policy

- Create:
  - if only repo name is given, create under `Atflow-Corp`
  - local clone path should default to `/Users/atflow/repos/<repo-name>`
- Clone:
  - if only repo name is given, clone `git@github.com:Atflow-Corp/<repo-name>.git`
  - local clone path should default to `/Users/atflow/repos/<repo-name>`

