# 부록 A: 주요 파일 인덱스

오마오를 읽을 때 먼저 열어 볼 파일 목록이다. 파일 이름은 기능 목록이 아니라 경계 목록으로 읽는다.

## 초기화와 플러그인 표면

- `src/index.ts`: plugin module entry, 5단계 초기화
- `src/plugin-interface.ts`: OpenCode hook handler 객체 생성
- `src/create-managers.ts`: 장기 상태 manager 생성
- `src/create-tools.ts`: skill context, category, tool registry 생성
- `src/create-hooks.ts`: core, continuation, skill hook 합성
- `src/plugin/types.ts`: 플러그인 내부 context와 record 타입

## 설정

- `src/plugin-config.ts`: JSONC load, migration, partial parse, merge
- `src/config/schema/oh-my-opencode-config.ts`: root Zod schema
- `src/config/schema/`: 기능별 config schema
- `src/cli/config-manager/`: install 시 설정 생성과 수정

## OpenCode handler

- `src/plugin/chat-message.ts`: 첫 메시지, keyword, session setup
- `src/plugin/chat-params.ts`: 모델 파라미터와 effort 조정
- `src/plugin/chat-headers.ts`: provider header 주입
- `src/plugin/event.ts`: 세션 생명주기와 runtime dispatch
- `src/plugin/tool-execute-before.ts`: 도구 실행 전 guard
- `src/plugin/tool-execute-after.ts`: 도구 실행 후 보정
- `src/plugin/messages-transform.ts`: 메시지 transform

## 에이전트와 도구

- `src/agents/builtin-agents.ts`: built-in agent 생성 진입점
- `src/agents/builtin-agents/`: model resolution, override, special agent config
- `src/tools/index.ts`: tool export와 기본 도구 묶음
- `src/plugin/tool-registry.ts`: 최종 tool registry 합성
- `src/tools/delegate-task/`: category 기반 하위 agent 위임
- `src/tools/hashline-edit/`: content hash 기반 edit

## 훅과 기능

- `src/plugin/hooks/create-session-hooks.ts`: session lifecycle hook
- `src/plugin/hooks/create-tool-guard-hooks.ts`: tool guard hook
- `src/plugin/hooks/create-transform-hooks.ts`: message transform hook
- `src/plugin/hooks/create-continuation-hooks.ts`: long-running task hook
- `src/features/background-agent/`: background execution manager
- `src/features/skill-mcp-manager/`: session scoped skill MCP client
- `src/features/claude-code-*`: Claude Code compatibility bridge

## 모델 데이터와 배포

- `src/mcp/`: built-in MCP
- `src/shared/model-capabilities/`: 모델 capability snapshot과 조회
- `src/shared/model-requirements.ts`: agent/category fallback chain
- `src/cli/`: install, run, doctor, mcp-oauth
- `script/`: build, schema, binary automation
- `packages/`: platform binary packages
