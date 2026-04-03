This directory is arranged to mirror `/Users/atflow/.openclaw`.

Key paths:

- config: `openclaw/openclaw.json`
- git policy: `openclaw/git-policy.md`
- platform standard: `openclaw/platform-standard.yaml`
- project registry template: `openclaw/projects.yaml`
- default workspace: `openclaw/workspace`
- PM workspace: `openclaw/workspace-pm`
- agent identity/rules: `openclaw/agents/<agent-id>/agent`
- workspace-level rules: `openclaw/workspace*/AGENTS.md`
- scaffold reference copied from `openclaw_workspaces`: `openclaw/WORKSPACES.md`

Current channel routing in `openclaw/openclaw.json`:

- Slack channel `C0AFYJXUQS0` -> `main` via Slack account `main`
- Slack channel `C0AQMENGSSH` -> `pm` via Slack account `pm`
- Slack channel `C0ARKPVJD7A` -> `research` via Slack account `research`

Slack behavior:

- `main`
  - DMs are allowed
  - invited channels are allowed
  - mention is required by default in channels
  - `#openclaw-requests` (`C0AFYJXUQS0`) is the exception and does not require mention
- `pm`
  - DMs are disabled
  - intended for `#openclaw-pm` only
- `research`
  - DMs are disabled
  - intended for `#openclaw-research` only

Operational note:

- To keep `pm` and `research` channel-scoped in practice, invite those Slack apps only to their dedicated channels.
- `main` can be invited broadly.
- With `allowBots` still disabled, `main` should use direct sub-agent delegation to call `pm` or `research`, not Slack bot-to-bot mentions.

Slack account env vars:

- `main`
  - `SLACK_APP_TOKEN`
  - `SLACK_BOT_TOKEN`
- `pm`
  - `SLACK_PM_APP_TOKEN`
  - `SLACK_PM_BOT_TOKEN`
- `research`
  - `SLACK_RESEARCH_APP_TOKEN`
  - `SLACK_RESEARCH_BOT_TOKEN`

Notes:

- The JSON keeps absolute paths as `/Users/atflow/.openclaw/...` by design, based on the assumption requested for this setup.
- In the current repository, this `openclaw/` directory is the filesystem stand-in for that path.
- Agent rules have been placed in both `agentDir` and each matching `workspace` root so role behavior can be picked up from either context.
- Git operations assume SSH auth is already configured for the `atflow` user.
- If a repo URL is omitted, repository names resolve to the `Atflow-Corp` GitHub organization by default.
- The default project stack is Django + Django templates + AWS, with SQLite for local/test and PostgreSQL for production.
- The default Python test stack is `pytest` with `pytest-cov`, `pytest-django`, `pytest-factoryboy`, `pytest-freezegun`, `pytest-mock`, `django-test-plus`, and `requests-mock`.
- If app development is needed, the default mobile stack is Flutter with GetX.
- Temporary public review URLs can be exposed from a local Django server using Tailscale Funnel, but production should still deploy to AWS.
