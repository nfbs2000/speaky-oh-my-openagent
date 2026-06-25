# 부록 H: 용어집

## 오마오

`oh-my-opencode`의 줄임말. OpenCode 위에서 실행되는 배터리 포함 플러그인 하니스다.

## Plugin surface

OpenCode가 플러그인에게 제공하는 handler 계약. `config`, `tool`, `chat.message`, `event`, `tool.execute.before` 등이 포함된다.

## Manager

훅 호출 하나보다 오래 살아야 하는 상태를 관리하는 객체. background, tmux, skill MCP, config handler, model fallback controller가 여기에 속한다.

## Hook tier

훅을 생명주기별로 나눈 계층. session, tool guard, transform, continuation, skill로 읽을 수 있다.

## Skill

에이전트가 사용할 수 있는 지식과 절차의 단위. tool과 달리 항상 실행 능력을 뜻하지 않는다.

## Skill MCP

스킬에 포함된 MCP 서버. 전역 MCP가 아니라 session scoped client로 관리된다.

## Hashline

Read 결과에 line number와 content hash 기반 ID를 붙여 edit의 stale context 위험을 줄이는 방식이다.

## Model fallback

모델 선택이나 provider 오류에 대응하는 proactive fallback.

## Runtime fallback

세션 실행 중 발생한 error 이벤트에 반응하는 fallback.
