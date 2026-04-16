---
title: "Gemini CLI 업데이트 핵심 정리 (v0.1 ~ v0.38.1)"
date: 2026-04-16
draft: false
tags: ["Gemini CLI", "Google", "AI", "CLI", "Changelog"]
summary: "Google Gemini CLI의 주요 업데이트를 버전별로 핵심만 추려 정리합니다. 모델 업그레이드, 신규 기능, 플랫폼 지원 등 메이저 변경사항을 한눈에 볼 수 있습니다. (v0.38.1 기준)"
---

> 원본: [google-gemini/gemini-cli Releases](https://github.com/google-gemini/gemini-cli/releases)
>
> 마지막 업데이트: 2026-04-16 (v0.38.1 기준)

---

## 모델 업그레이드 이력

| 버전 | 모델 변경 |
|------|----------|
| [v0.37.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.37.0) | `AuthType.GATEWAY`를 Gemini 3.1 Pro/Flash Lite로 기본 고정, 모든 사용자 티어에 Flash Lite Preview 노출 |
| [v0.36.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.36.0) | `ModelConfigService` 중앙화, Gemini Flash 3.1 Lite 실험 플래그 지원, Gemini 3.1 Pro → customtools 동적 라우팅 |
| [v0.35.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.35.0) | `ModelConfigService` 동적 모델 해석, Pro 모델 사용량 가드, 플랜 모드 종료 시 Flash 폴백 |
| [v0.34.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.34.0) | `ModelConfigService`에 `ModelChain` 지원, 동적 ModelDialog |
| [v0.31.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.31.0) | **Gemini 3.1 Pro Preview 지원**, 모델 패밀리별 도구 모듈화, Gemma 라우터 실험 (LiteRT-LM shim) |
| [v0.29.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.29.0) | `previewFeatures` 플래그 제거 → **Gemini 3 기본값**, 내부 유틸리티 모델 Gemini 3 이관, chat 모델 미인식 시 `chat-base` 폴백 |
| [v0.28.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.28.0) | 멀티모달 도구 응답 토큰 계산 최적화, `GOOGLE_GENAI_API_VERSION` 환경변수 |
| [v0.27.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.27.0) | 모델 패밀리별 시스템 프롬프트, Gemini 3 라우팅용 숫자 복잡도 스코어링 A/B |
| [v0.25.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.25.0) | Flash Lite 유틸리티 폴백 체인, 서브에이전트 모델 라우팅 배선, `auto` 모델 별칭 |
| [v0.16.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.16.0) | **Gemini 3 모델 출시** |

---

## Major Feature Release

| 버전 | 카테고리 | 핵심 기능 | 설명 |
|------|---------|----------|------|
| [v0.38.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.38.0) | Agent | **ContextCompressionService & 백그라운드 메모리** | `ContextCompressionService`로 컨텍스트 자동 압축, 스킬 추출용 백그라운드 메모리 서비스, `AsyncLocalStorage` 기반 서브에이전트 워크스페이스 스코핑, 컨텍스트 인지형 지속 정책 승인, 백그라운드 프로세스 모니터링 도구 |
| [v0.38.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.38.0) | UX | **TerminalBuffer flicker-free** | flicker 해결을 위한 TerminalBuffer 모드, 토픽 선택적 확장 및 클릭 확장, 프롬프트 입력창 스크롤바, 기본 `Ctrl+X` → `Ctrl+G` 전환 |
| [v0.37.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.37.0) | UX | **Tab-to-queue & 확장 업데이트 UI** | 생성 중에 `Tab`으로 메시지 큐잉, 컴팩트 도구 출력, 확장 업데이트 UI, footer에 인증 정보 표시, CI 스킬 및 behavioral-evals 스킬 추가 |
| [v0.36.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.36.0) | Context | **Chapters (토픽 그룹핑) & Worktree** | 도구 기반 토픽 그룹핑(Chapters), 토픽 내레이션, `save_memory` 대체 memory manager agent, 통합 컨텍스트 관리, **Git worktree로 격리된 병렬 세션**, 브라우저 에이전트 개인정보 동의·민감 액션 제어 |
| [v0.35.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.35.0) | Security | **Windows 네이티브 샌드박스 & 커스텀 키바인딩** | Windows 네이티브 샌드박싱, 동적 Linux/macOS 샌드박스 확장, `SandboxManager` stateless 아키텍처, 커스터마이징 가능한 키보드 단축키, `--admin-policy`/`--policy` 플래그, 안전 도구 동시 실행, 서브에이전트 기본 활성화 |
| [v0.34.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.34.0) | Platform | **esbuild 번들 & gVisor 샌드박스** | npm 패키지에 esbuild 번들 출하, 독립 실행 바이너리, 네이티브 gVisor(runsc) 샌드박싱, Linux bubblewrap+seccomp, strict macOS Seatbelt, 플랜 모드 기본 활성화, 통합 `KeychainService`, 음성 친화 응답 포맷터 |
| [v0.33.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.33.0) | UX | **헤더 재디자인 & 30일 보관** | ASCII 아이콘 컴팩트 헤더, `/plan copy` 서브커맨드, 서브에이전트 활동 UX, 채팅 기록 기본 30일 보관, A2A 에이전트 카드 HTTP 인증, 확장 매니페스트 `plan` 디렉토리 |
| [v0.32.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.32.0) | Automation | **비대화형 플랜 모드 & 대화형 쉘 자동완성** | 플랜 모드 비대화형 실행, 외부 에디터로 플랜 편집, 대화형 쉘 자동완성, low/full CLI 에러 상세 수준 모드, G1 AI 크레딧 초과 플로우 |
| [v0.31.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.31.0) | Browser | **실험적 브라우저 에이전트 & 웹 fetch** | 실험적 브라우저 에이전트, 실험적 직접 웹 fetch, MCP 진행 업데이트, `RuntimeHook` 함수 지원, macOS run-event 알림, xterm.js 렌더링 마이그레이션, `grep_search` → `read_file` 파이프라이닝 |
| [v0.30.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.30.0) | SDK | **Gemini CLI SDK 부트스트랩** | 초기 SDK 패키지, `SessionContext` SDK 도구 호출, 동적 시스템 인스트럭션, 커스텀 스킬 지원, 5단계 순차 계획 워크플로우 공식화, Vim 모드 완성도 향상, Solarized 테마 |
| [v0.29.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.29.0) | Plan | **플랜 모드 stable 승격** | `/plan` 슬래시 커맨드, 5단계 플래닝 워크플로우, 자동 모델 전환, 확장 레지스트리 클라이언트, 커스텀 테마 확장, 확장 링크 |
| [v0.28.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.28.0) | Agent | **백그라운드 쉘 & DevTools 통합** | `enter_plan_mode` 도구, 백그라운드 쉘 커맨드, 도구 출력 마스킹, `gemini-cli-devtools` F12 통합, 단축키 힌트 패널, Linux 크로스플랫폼 이미지 붙여넣기 |
| [v0.27.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.27.0) | UX | **`/plan` 커맨드 & JetBrains 지원** | `/plan`·`/rewind`·`/oncall`·`/commands reload`·`/extensions config`, `exit_plan_mode` 도구, 지속 `approvalMode`, `Shift+Tab` Plan Mode 순환, `AskUser` 도구, JetBrains·Positron·Sublime Text 탐지, 쉘 `background` 모드 |
| [v0.26.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.26.0) | Skills | **skill-creator & Plan Mode 실험** | 빌트인 `skill-creator` 스킬, 스킬 설치 동의 프롬프트, 실험적 `plan` 승인 모드, 엄격한 read-only 정책, `generalist` 에이전트, `/introspect` 커맨드, 이벤트 기반 도구 실행 스케줄러 |
| [v0.25.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.25.0) | Skills | **Agent Skills 기반 구축** | 다중 스코프 Skills 활성화, Skill 설치/제거 CLI, 빌트인 스킬 지원, frontmatter 마크다운 파서, `/agents` 슬래시 커맨드와 refresh·enable·disable, Rewind 데이터 구조 및 훅, 동적 터미널 탭 타이틀, `/bug` 이슈 프리필 |
| [v0.23.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.23.0) | Integration | 공식 ACP SDK & 원격 에이전트 | 공식 ACP SDK 적용, HTTP/SSE MCP 서버, 원격 에이전트 인프라, `/auth logout` |
| [v0.16.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.16.0) | Model | **Gemini 3 출시** | Gemini 3 모델 지원 |
| [v0.14.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.14.0) | Security | 확장 리로드 & MCP 정책 엔진 | 확장 리로드, 서브에이전트 압축, MCP 정책 엔진 보안 수정 |
| [v0.12.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.12.0) | UX | YOLO 비활성 설정 & 확장 별칭 | YOLO 모드 비활성화 설정, 확장 별칭 |
| [v0.10.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.10.0) | Tool | Todos 도구 & 대화형 쉘 기본 | Todos 도구, 대화형 쉘 기본 활성화 |
| [v0.9.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.9.0) | Agent | **서브에이전트 도입** | `enableSubagents` 설정으로 서브에이전트 첫 도입 |
| [v0.7.0](https://github.com/google-gemini/gemini-cli/releases/tag/v0.7.0) | Extensibility | MCP OAuth & 확장 릴리스 플로우 | MCP OAuth 인증 UI, 확장 릴리스 플로우 |
| [v0.2.2](https://github.com/google-gemini/gemini-cli/releases/tag/v0.2.2) | IDE | Zed ACP 통합 프리뷰 | Zed ACP 통합 프리뷰, Kitty 키보드 프로토콜 |
| [v0.1.22](https://github.com/google-gemini/gemini-cli/releases/tag/v0.1.22) | IDE | 초기 IDE 모드 & VS Code 확장 | IDE 모드, `/chat save`, VS Code 컴패니언 확장 |

---

## 주요 키보드 단축키 변경 이력

| 버전 | 변경 내용 |
|------|----------|
| v0.38.0 | 기본 외부 에디터 단축키 `Ctrl+X` → `Ctrl+G` 변경 |
| v0.37.0 | 생성 중에 `Tab`으로 메시지 큐잉, HooksDialog에 `Esc` 풋터 안내 |
| v0.36.0 | 입력 버퍼가 비어 있지 않으면 `Ctrl+D`로 종료 차단, 쉘 모드에서 `Esc`가 요청 취소하지 않도록 수정 |
| v0.35.0 | **커스터마이징 가능한 키보드 단축키 시스템**, 리터럴 문자 키바인딩, `-` 접두사로 키바인딩 제거, settings 다이얼로그 j/k 내비게이션 |
| v0.34.0 | `/compact`가 `/compress` 별칭으로 추가, 붙여넣기 시 `@` 이스케이프(의도치 않은 파일 확장 방지) |
| v0.30.0 | Vim X, `~`, r, f/F/t/T, df/dt 모션, y/p/P yank/paste, `Ctrl+O` 확장 힌트 통합 |
| v0.29.0 | Vim W/B/E 모션, Vim 모드가 insert 모드로 시작, 대화형 쉘 설정 조건부 `Ctrl+F` |
| v0.28.0 | Windows SS3 `Shift+Tab`, `Alt+D` 전방 단어 삭제, `Ctrl+O` 붙여넣기 플레이스홀더 확장, `Ctrl+Z` suspend 지원 |
| v0.27.0 | `Shift+Tab`으로 Plan Mode 순환, undo/redo를 `Cmd+Z`/`Alt+Z` 및 `Shift+Cmd+Z`/`Shift+Alt+Z`로 변경, 붙여넣기 플레이스홀더 더블클릭 확장 |
| v0.26.0 | `Esc-Esc`로 프롬프트 클리어, `Ctrl+Enter`/`Ctrl+J` 줄바꿈 수정 |
| v0.25.0 | `Tab`으로 쉘/입력창 포커스 전환, `Ctrl+X`에서 선호 에디터 사용, bracketed paste 항상 활성화, Kitty Shift+Space 지원 |

---

## 플랫폼 & 인프라 지원 확대

| 버전 | 플랫폼 | 내용 |
|------|--------|------|
| v0.38.0 | Windows | vim 에디터 PATH 없을 때 크래시 수정, 스킬 링크에 디렉토리 정션 사용, Windows 샌드박스 네이티브 `__write` 수정 |
| v0.37.0 | Linux | `ARG_MAX` 크래시 방지를 위한 linux 샌드박스 리팩터링, CI에 bubblewrap 설치 |
| v0.36.0 | IDE | VS Code 트래픽 통합 User-Agent, 세션 격리, 민감 액션 제어 |
| v0.35.0 | Windows | **Windows 네이티브 샌드박싱**, 동적 샌드박스 확장, `GeminiSandbox` Mandatory Integrity Control |
| v0.35.0 | macOS | 동적 Seatbelt 확장, worktree 지원, `ARG_MAX` 방지용 프로파일 파일 배칭 |
| v0.35.0 | Linux | 동적 샌드박스 확장, worktree 지원 |
| v0.34.0 | Release | npm 패키지에 esbuild 번들 출하, 독립 실행 바이너리 빌드, BSD shebang (`-S` 제거), macOS Terminal.app 테마 대비 개선 |
| v0.34.0 | Auth | **통합 `KeychainService`** 토큰 저장소 마이그레이션, 인증 실패 graceful 처리, 'sign in'/'sign out' 용어 통일, auth type `oauth2` → `oauth` |
| v0.33.0 | Sandbox | strict Seatbelt 프로파일, Linux bubblewrap 샌드박스, Linux seccomp, LXC 컨테이너 샌드박스 |
| v0.31.0 | Terminal | Windows Terminal Kitty 코드 활성화 수정, CJK 입력과 Full Unicode 스칼라, Devtools 모노레포 이관 |
| v0.30.0 | Perf | 장시간 세션 OOM 수정, `loadSettings`/`loadApiKey` 캐시, `refreshAuth` 쿼터·실험 병렬화, `--version` 시작 시간 최적화, IDE 클라이언트 백그라운드화 (~3.5s 단축), 코드 스플리팅 및 UI 지연 로드 |
| v0.30.0 | Terminal | xterm.js 렌더러 마이그레이션, TrueColor 감지, macOS Terminal.app 테마 대비 개선 |
| v0.29.0 | macOS | 대화형 세션 run-event 알림 |
| v0.29.0 | Windows | `robustRealpath` EISDIR 처리, 라인 엔딩·경로 구분자 버그 수정 |
| v0.28.0 | IDE | DevTools 통합 (`gemini-cli-devtools`, F12), 백그라운드 쉘 포커스 내비게이션 개선 |
| v0.28.0 | Perf | 토큰 계산 최적화 (멀티모달), `stripUnsafeCharacters` regex 최적화, 테이블 렌더링 메모이제이션 |
| v0.28.0 | Windows | Windows 전용 에이전트 품질 및 시스템 프롬프트, `shell: true` `.cmd` EINVAL 수정 |
| v0.27.0 | IDE | **JetBrains 감지, Positron IDE, Sublime Text, Antigravity 터미널**, `GEMINI_CLI_IDE_PID` |
| v0.27.0 | Terminal | 리사이즈 중 alternate buffer 렌더 안정화, iTerm alt buffer 배경 렌더 수정, 도구 출력 JSON pretty 렌더링 |
| v0.26.0 | Auth | OAuth `127.0.0.1` 사용 (localhost 대신), RFC 9728 경로 기반 OAuth 리소스 디스커버리, PKCE 길이 수정 |
| v0.26.0 | Terminal | Windows Terminal OSC-52 클립보드 복사, 터미널 capability 쿼리 hidden sequence 래핑 |
| v0.25.0 | Terminal | `TERM=xterm-256color` 강제, `modifyOtherKeys` 추론, OSC52 SSH/WSL 한정, Hx 에디터 지원 |
| v0.23.0 | MCP | HTTP/SSE MCP 서버 공식 지원, 원격 에이전트 인프라 |
| v0.2.2 | IDE | Zed ACP 통합 프리뷰 |
| v0.1.22 | IDE | VS Code 컴패니언 확장 |

---

## SDK / API 주요 변경

| 버전 | 변경 내용 |
|------|----------|
| v0.38.0 | 환경변수 기본값 지원, 전역 환경변수 allowlist 준수, 환경변수 리댁션 비활성화 옵션, ACP `/about`·`/help` 커맨드, 첨부 허가 프롬프트, `maxActionsPerTask` 브라우저 에이전트 |
| v0.37.0 | `experimental.adk.agentSessionNoninteractiveEnabled`, `general.plan.directory` 정책, `agentCardJson` 원격 에이전트 인라인, 플랜 모드에서 `complete_task` 허용, `BeforeModel` hook 모델 오버라이드 전파 |
| v0.36.0 | 'ask' decision BeforeTool hooks, 서브에이전트 `tools` 필터링, 폴더 신뢰 강제 옵션, `toolSandboxing` 설정, `forbiddenPaths` GlobalSandboxOptions |
| v0.35.0 | `--admin-policy`/`--policy` 플래그, `directory tree context` 설정, `discoveryMaxDirs` 전역 config 전달, JIT 컨텍스트 기본 활성화, `useAlternateBuffer` config 토글 |
| v0.34.0 | `ModelDefinitions`/`ModelChain` 스키마, `memoryManager` 기본 false, `disableJITContextLoading` 기본값, `UnifiedContextManagement` 스키마, `--acp` (rename from `--experimental-acp`), `--all` 확장 uninstall |
| v0.33.0 | ACP SDK 0.12→0.16.1 업그레이드, `set models` 인터페이스, 확장 매니페스트 `plan` 디렉토리, 확장 정책 엔진, ACP `/memory`·`/init`·`/extensions`·`/restore` 슬래시 커맨드 핸들링 |
| v0.31.0 | SDK 세션 기반 아키텍처, `MCPOAuthProvider`가 MCPSDK `OAuthClientProvider` 구현, MCP 진행 바·스로틀링·입력 검증, MCP 서버 와일드카드 정책 엔진, 도구 annotation 매칭 정책 |
| v0.30.0 | **초기 SDK 패키지 부트스트랩**, `SessionContext` SDK 도구 호출, 동적 시스템 인스트럭션, 커스텀 스킬, `general.plan.directory`, `loadingPhrases` enum, `RuntimeHook` 함수, A2A `allowedTools` |
| v0.29.0 | `strictModeDisabled` (rename of `secureModeEnabled`), 프로젝트 수준 정책, `disableAlwaysAllow`, `maxAttempts` 재시도, `extensionRegistryURI`, `memoryBoundaryMarkers`, admin MCP allowlist |
| v0.28.0 | `--allowed-tools`/`excludeTools` deprecate → 정책 엔진, `--yolo` 더 이상 headless 강제 안 함, `--model` 검증, `GOOGLE_GEMINI_BASE_URL`/`GOOGLE_VERTEX_BASE_URL` 샌드박스 전파, `CODE_ASSIST_API_VERSION` env, `useAlternateBuffer`·`experimental.useOSC52Copy` 설정, AfterTool tail tool calls |
| v0.27.0 | `search_file_content` → `grep_search` 리네임 (별칭 유지), replace 도구 `expected_replacements` → `allow_multiple`, `grep_search include` → `include_pattern`, `read_file` 1-based `start_line`/`end_line`, `beforeTool`/`afterTool` → `hookSystem` 마이그레이션, hooks 기본 활성화, ACP `ToolKind` 매핑, ACP 세션 resume |
| v0.26.0 | 실험적 확장 설정, `list_changed` MCP 알림으로 프롬프트 갱신 |
| v0.25.0 | `GEMINI_CLI_HOME` 엄격 테스트 격리, `GEMINI_EXP` 로컬 실험 오버라이드, `GOOGLE_GENAI_API_VERSION`, `disableLLMCorrection`, 음성 부정 네이밍 → 긍정 네이밍 (`disable*` → `enable*`), 모델 훅 명시적 stop/block 실행 제어, `mcp_context`를 `BeforeTool`/`AfterTool` 입력에 추가 |

---

## 보안 관련 주요 패치

| 버전 | 내용 |
|------|------|
| v0.38.0 | 미니멀 샌드박스 상태 라벨, 프로젝트 ignore 파일 기반 샌드박스 금지 경로 채움, Core File System 안전하지 않은 type assertion 수정, Gemini 3.1 정책 체인 지원 |
| v0.37.0 | 컨텍스트 인지형 지속 정책 승인, 플랜 모드에서 `web_fetch`를 ask_user로만 명시 허용, 전역 temp 디렉토리를 샌드박스 허용 경로에 포함, 서브에이전트 격리·정리 강화, `argsPattern` 보안 강화 |
| v0.36.0 | 정책 config `toolName` 강제, OS별 샌드박스 매니저에 `forbiddenPaths` 도입, 동적 권한 확장 통합 테스트, 도구 확인 UI 개선, 프로액티브 확장 승인 매칭 수정 |
| v0.35.0 | **브라우저 도메인 제한**: embedded URL 탐지로 `allowedDomains` 우회 방지, 프록시 우회 제약, 자동화 중 브라우저 입력 차단 오버레이, 서브에이전트 사고 내용 살균, 도메인 위반 시 서브에이전트 종료, 관리자 강제 MCP 서버 설치 |
| v0.34.0 | Linux bubblewrap + seccomp 샌드박스, strict macOS Seatbelt allowlist, 샌드박스 거부 파싱 위임, IP 검증 및 safeFetch 기반, `SandboxManager` stateless 아키텍처, 확장 업데이트 암호학적 무결성 검증 |
| v0.33.0 | **확장 업데이트 암호학적 무결성 검증**, `--admin-policy` 보조 관리 정책 플래그, 플랜 모드 서브에이전트 우회 방지, 서브에이전트 TOML 정책, 거버넌스 파일 샌드박스 "Write-Protected" |
| v0.32.0 | `logPrompts` 프라이버시 강화 (메모리 누수 수정 포함), 침입적 MCP 에러 감소 |
| v0.31.0 | 서브에이전트 컨텍스트를 정책 엔진에 전파, `/directory add` 통합 폴더 신뢰 강제, MCP 도구 FQN 살균·길이 제한, MCP 서버 와일드카드 정책, 도구 annotation 매칭 정책, 폴더 신뢰 개선 |
| v0.30.0 | 이미지 패키지 무결성 검증 강화, 치명적 의존성 취약점 패치, `minimatch`·`cross-spawn` 고위험 CVE, Conseca 보안 프레임워크 도입 |
| v0.29.0 | 브라우저 에이전트 보안 프롬프트, env 파일 시크릿 가시성 잠금, 안전하지 않은 cloning 제거, 기만적 유니코드 문자 제거, 기만적 URL 탐지, `web_fetch` rate-limit (프롬프트 인젝션 DDoS 완화) |
| v0.28.0 | MCP 서버로의 자격 증명 노출 수정, 워크스페이스 설정·스킬·컨텍스트에 폴더 신뢰 강제, 신뢰 폴더 원자적 쓰기·안전 검사, 로컬 확장 설치 시 폴더 신뢰 강제, MCP OAuth 사용자 동의 필수, headless 모드 폴더 신뢰 비활성화 |
| v0.27.0 | 스킬 설치 보안 동의 프롬프트, 훅 주입 컨텍스트를 별도 XML 태그로 래핑, 비대화형 출력 ANSI 이스케이프 살균 |
| v0.26.0 | 커맨드 이름·설명 살균, 엄격한 정책 디렉토리 권한, GitHub Actions 리댁션 상시 활성화, git 원격 URL PAT 토큰 처리 |
| v0.25.0 | 쉘 커맨드 안전성 및 파싱 강제 |
| v0.14.0 | MCP 정책 엔진 보안 수정 |

---

> 이 페이지는 [Gemini CLI Releases](https://github.com/google-gemini/gemini-cli/releases)를 기반으로 주요 변경사항만 발췌하여 정리한 것입니다. 전체 내용은 원본을 참고하세요.
