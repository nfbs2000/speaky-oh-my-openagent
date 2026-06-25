# 부록 E: 빌드와 테스트 명령 모음

오마오 저장소는 Bun을 기준으로 한다. npm이나 yarn 대신 Bun 명령을 사용한다.

## 기본 검증

```bash
bun test
bun run typecheck
bun run build
```

## 전체 빌드

```bash
bun run build:all
```

이 명령은 plugin build, declaration, schema, platform binary build를 포함한다.

## 모델 capability 관련 테스트

```bash
bun run test:model-capabilities
```

모델 fallback과 agent model requirement를 건드렸다면 이 경로를 우선 확인한다.

## CLI 사용

```bash
bunx oh-my-opencode install
bunx oh-my-opencode doctor
bunx oh-my-opencode run
```

## 책 빌드

```bash
mdbook build docs/book-ko
mdbook serve docs/book-ko --open
```

## 검색 인덱스

```bash
npx pagefind --site docs/book-ko/book
```

## 로그 확인

```bash
tail -f /tmp/oh-my-opencode.log
```

플러그인 로딩, config handler, warning, fallback 추적에 유용하다.
