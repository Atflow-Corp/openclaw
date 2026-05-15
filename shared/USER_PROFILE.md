# Shared User Profile

This file is the shared source of truth for stable user and team identity across all OpenClaw agents.

Usage rules:
- Read this file before asking who the user is or how to address them.
- If a stable profile detail is missing here, prefer a neutral response instead of repeatedly asking the user to reintroduce themselves.
- If the user explicitly provides a stable profile update, reflect it here so other agents can reuse it.

Known defaults:
- Preferred response language: Korean
- Team language: Korean
- English technical terms: allowed when clearer or standard
- Timezone: Asia/Seoul

Profile:
- Name: 김호승 (Seba)
- Preferred form of address: 세바 (Seba), CTO
- Role: CTO
- Team: 앳플로우 (Atflow)
- Slack ID: U07AY5MD3MM
- Email: seba@atflow.kr

- Name: 이선영
- Preferred form of address: 선영님, CEO
- Role: CEO
- Team: 앳플로우 (Atflow)
- Email: stacey@atflow.kr

Notes:
- 김호승님은 본인을 세바(Seba)라고 부르는 것을 선호함.
- 이선영님은 앳플로우의 CEO이며 기획, 디자인, 개발 등 다방면에 능통한 올라운더임.
- 팀원들의 휴가는 `앳플로우_휴가공유` 캘린더에서 확인 가능함.
- The team is Korean, so default user-facing responses should be in Korean.
- Repository creation preference: By default, always create GitHub repositories as Private unless explicitly asked to make them Public.
- Path interpretation preference: Unless a different path is explicitly provided, treat mentions of `~/repos`, `repos`, `레포에서`, `repo에서`, or `그 레포` as referring to `/Users/atflow/repos`.
- Main, PM, Research, and delegated specialist agents should reuse this profile instead of asking duplicate identity questions.
