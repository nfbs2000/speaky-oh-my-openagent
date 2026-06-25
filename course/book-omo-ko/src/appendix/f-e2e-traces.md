# 부록 F: 엔드투엔드 사례 추적

## 사례 1: 플러그인 로딩

1. OpenCode가 `pluginModule.server(input, options)`를 호출한다.
2. `loadPluginConfig`가 사용자와 프로젝트 JSONC를 읽는다.
3. `createManagers`가 tmux, background, skill MCP, config handler를 만든다.
4. `createTools`가 skill context와 tool registry를 만든다.
5. `createHooks`가 core, continuation, skill hook을 만든다.
6. `createPluginInterface`가 OpenCode handler 객체를 반환한다.

## 사례 2: 하위 에이전트 위임

1. 모델이 `task` 또는 `delegate-task` 도구를 선택한다.
2. 도구가 category, agent overrides, available skills를 참고한다.
3. BackgroundManager가 subagent session을 만든다.
4. TmuxSessionManager가 세션과 pane을 추적한다.
5. task toast와 parent notification 상태가 갱신된다.
6. 사용자는 `background_output` 또는 notification으로 진행을 본다.

## 사례 3: Hashline edit

1. Read 결과가 hashline read enhancer를 지난다.
2. 각 줄에 `LINE#ID`가 붙는다.
3. 모델이 hashline edit tool에 대상 ID와 변경 내용을 제출한다.
4. 도구가 현재 파일 내용의 hash와 제출된 ID를 비교한다.
5. mismatch면 거절하고, match면 수정한다.

## 사례 4: Skill MCP 호출

1. 모델이 `skill_mcp` tool을 호출한다.
2. tool이 현재 sessionID와 skill/server 이름을 만든다.
3. SkillMcpManager가 session scoped client를 얻는다.
4. OAuth step-up이나 refresh가 필요하면 manager가 처리한다.
5. tool, resource, prompt 결과가 모델에게 돌아간다.

## 사례 5: Runtime fallback

1. OpenCode session에서 error 이벤트가 발생한다.
2. event handler가 runtime fallback hook에 전달한다.
3. hook이 설정된 error code와 timeout 정책을 확인한다.
4. 재시도 또는 대체 실행이 가능하면 적용한다.
5. 사용자는 toast, title, log로 fallback 흔적을 확인할 수 있다.
