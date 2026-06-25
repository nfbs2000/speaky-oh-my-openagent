# 부록 B: 에이전트, 훅, 도구 인덱스

## 주요 에이전트

- `sisyphus`: orchestration과 위임 중심 agent
- `hephaestus`: 구현 중심 agent
- `oracle`: 분석과 판단 중심 agent
- `librarian`: 코드베이스 탐색과 정보 수집
- `explore`: 탐색 전용 agent
- `atlas`: 계획, 진행, continuation 추적
- `prometheus`: 계획과 품질 기준
- `metis`: 전략과 조율
- `momus`: 리뷰와 비판적 점검
- `multimodal-looker`: 이미지와 multimodal 입력
- `sisyphus-junior`: 경량 하위 작업

## 훅 티어

- session: context window, recovery, notification, think mode, fallback, update, start-work
- tool guard: comment checker, output truncator, rules injector, write guard, hashline enhancer
- transform: Claude Code hooks, keyword detector, context injector, thinking block validator, tool pair validator
- continuation: stop guard, compaction injector, todo preserver, todo enforcer, background notification, atlas
- skill: category skill reminder, auto slash command

## 주요 도구

- 코드 탐색: `glob`, `grep`, `ast_grep_search`, `lsp_symbols`, `lsp_goto_definition`
- 코드 수정: `edit`, `ast_grep_replace`, `lsp_rename`
- 에이전트 실행: `call_omo_agent`, `task`
- 백그라운드: `background_output`, `background_cancel`
- 세션: `session_list`, `session_read`, `session_search`, `session_info`
- 스킬: `skill`, `skill_mcp`
- task system: `task_create`, `task_get`, `task_list`, `task_update`
- shell: `interactive_bash`

## 읽는 순서

에이전트는 `src/agents/builtin-agents.ts`에서 시작한다. 훅은 `src/create-hooks.ts`에서 시작해 `src/plugin/hooks/create-*-hooks.ts`로 내려간다. 도구는 `src/plugin/tool-registry.ts`에서 최종 노출 목록을 확인한다.
