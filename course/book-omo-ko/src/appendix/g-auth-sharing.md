# 부록 G: 인증, MCP, provider 데이터

오마오는 인증과 외부 데이터를 세 영역에서 다룬다.

## MCP 인증

Skill MCP와 일부 remote MCP는 OAuth를 필요로 할 수 있다. `SkillMcpManager`는 post-request auth error와 step-up을 처리하고, 필요하면 client reconnect를 수행한다.

관련 소스:

- `src/features/skill-mcp-manager/`
- `src/features/mcp-oauth/`
- `src/cli/mcp-oauth/`

## 환경 변수

Claude Code `.mcp.json`의 `${VAR}` expansion은 allowlist를 통과해야 한다. `mcp_env_allowlist`는 사용자 config에서 관리된다. 환경 변수 노출은 프로젝트보다 개인 환경에 가까운 정책이기 때문이다.

관련 소스:

- `src/features/claude-code-mcp-loader/env-expander.ts`
- `src/features/claude-code-mcp-loader/configure-allowed-env-vars.ts`

## provider와 모델 데이터

provider 설정은 `applyProviderConfig()`에서 context limit cache와 vision capable model cache로 바뀐다. 모델 capability 데이터는 generated snapshot과 refresh CLI를 통해 갱신된다.

관련 소스:

- `src/plugin-handlers/provider-config-handler.ts`
- `src/shared/model-capabilities/`
- `src/cli/refresh-model-capabilities.ts`
