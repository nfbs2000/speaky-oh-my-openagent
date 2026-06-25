# 부록 C: 구성 크로스워크

오마오 설정은 사용자 config와 프로젝트 config를 합쳐 최종 runtime config가 된다.

## 파일 위치

- 사용자: `~/.config/opencode/oh-my-opencode.jsonc`
- 프로젝트: `.opencode/oh-my-opencode.jsonc`
- legacy 이름: migration을 통해 canonical 이름으로 옮겨진다.

## 병합 규칙

| 필드 | 규칙 | 이유 |
| --- | --- | --- |
| `agents` | deep merge | agent별 override를 부분 적용 |
| `categories` | deep merge | built-in category와 custom category 공존 |
| `claude_code` | deep merge | 호환성 기능별 부분 조정 |
| `disabled_agents` | set union | 사용자와 프로젝트의 비활성화 의도 보존 |
| `disabled_hooks` | set union | 위험하거나 중복되는 hook 비활성화 |
| `disabled_mcps` | set union | MCP 출처별 제외 정책 |
| `disabled_skills` | set union | skill 가시성 제어 |
| `disabled_commands` | set union | workflow 메뉴 제어 |
| `disabled_tools` | set union | 실행 표면 축소 |
| `mcp_env_allowlist` | 사용자 config 우선 | env 노출은 개인 환경에 가깝다 |
| 기타 필드 | override | 프로젝트 정책이 base를 대체 |

## 대표 기능 필드

- `hashline_edit`: hashline edit tool과 read enhancer 활성화
- `model_fallback`: proactive model fallback 활성화
- `runtime_fallback`: session error 기반 fallback 설정
- `background_task`: background agent 동시성, timeout, sync 관련 설정
- `tmux`: tmux session integration
- `skills`: skill discovery와 loader 동작
- `websearch`: built-in websearch MCP 설정
- `experimental`: max tools, safe hook creation, preemptive compaction 등 실험 기능

## 진단 명령

```bash
bunx oh-my-opencode doctor
```

설정이 이상할 때는 schema 오류, provider/model 해상도, binary 상태를 doctor에서 먼저 확인한다.
