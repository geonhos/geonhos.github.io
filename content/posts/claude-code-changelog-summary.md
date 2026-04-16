---
title: "Claude Code 업데이트 핵심 정리 (v1.0 ~ v2.1.110)"
date: 2026-04-16
draft: false
tags: ["Claude Code", "Anthropic", "AI", "CLI", "Changelog"]
summary: "Claude Code의 주요 업데이트를 버전별로 핵심만 추려 정리합니다. 모델 업그레이드, 신규 기능, 플랫폼 지원 등 메이저 변경사항을 한눈에 볼 수 있습니다. (v2.1.110 기준)"
---

> 원본: [anthropics/claude-code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
>
> 마지막 업데이트: 2026-04-16 (v2.1.110 기준)

---

## 모델 업그레이드 이력

| 버전 | 모델 변경 |
|------|----------|
| [v2.1.77](https://github.com/anthropics/claude-code/releases/tag/v2.1.77) | Opus 4.6 기본 최대 출력 64k 토큰, Opus 4.6·Sonnet 4.6 상한 128k 토큰으로 확대 |
| [v2.1.75](https://github.com/anthropics/claude-code/releases/tag/v2.1.75) | Opus 4.6 **1M 컨텍스트 윈도우 기본 적용** (Max/Team/Enterprise) |
| [v2.1.73](https://github.com/anthropics/claude-code/releases/tag/v2.1.73) | Bedrock/Vertex/Foundry 기본 Opus를 4.6으로 변경 (기존 4.1) |
| [v2.1.94](https://github.com/anthropics/claude-code/releases/tag/v2.1.94) | 기본 effort를 **high로 상향** (API-key·Bedrock/Vertex/Foundry·Team·Enterprise) |
| [v2.1.68](https://github.com/anthropics/claude-code/releases/tag/v2.1.68) | Opus 4.6 기본 effort를 medium으로 변경 (Max/Team), Opus 4·4.1 퇴출 |
| [v2.1.45](https://github.com/anthropics/claude-code/releases/tag/v2.1.45) | Claude Sonnet 4.6 지원 |
| [v2.1.36](https://github.com/anthropics/claude-code/releases/tag/v2.1.36) | Opus 4.6 Fast mode 지원 |
| [v2.1.32](https://github.com/anthropics/claude-code/releases/tag/v2.1.32) | **Claude Opus 4.6** 출시 |
| [v2.0.51](https://github.com/anthropics/claude-code/releases/tag/v2.0.51) | **Opus 4.5** 출시, Pro 사용자 extra usage로 사용 가능 |
| [v2.0.17](https://github.com/anthropics/claude-code/releases/tag/v2.0.17) | Haiku 4.5 모델 셀렉터 추가, Explore subagent에 Haiku 적용 |
| [v1.0.69](https://github.com/anthropics/claude-code/releases/tag/v1.0.69) | Opus 4.1로 업그레이드 |

---

## Major Feature Release

| 버전 | 카테고리 | 핵심 기능 | 설명 |
|------|---------|----------|------|
| [v2.1.110](https://github.com/anthropics/claude-code/releases/tag/v2.1.110) | UX | **`/tui` 전환 & Push Notification** | `/tui fullscreen`으로 동일 세션 내 flicker-free 렌더링 전환, 모바일 푸시 알림 도구 추가 (Remote Control + "Push when Claude decides" 설정 시), `Ctrl+O`를 verbose transcript 토글로 단순화하고 포커스 뷰는 `/focus`로 분리, `/plugin` 설치 탭 개선 |
| [v2.1.108](https://github.com/anthropics/claude-code/releases/tag/v2.1.108) | UX | **`/recap` 세션 복귀 & 1시간 캐시** | `/recap`으로 세션 복귀 시 컨텍스트 요약, `ENABLE_PROMPT_CACHING_1H`로 1시간 프롬프트 캐시 TTL 옵트인 (API-key·Bedrock·Vertex·Foundry), 모델이 `/init`·`/review`·`/security-review` 등 빌트인 슬래시 커맨드를 Skill 도구로 호출 가능, `/undo`=`/rewind` 별칭, 언어 grammar on-demand 로딩으로 메모리 절감 |
| [v2.1.105](https://github.com/anthropics/claude-code/releases/tag/v2.1.105) | Automation | **PreCompact 차단 & 플러그인 모니터** | PreCompact hook에서 compaction 차단 가능 (exit 2 또는 `{"decision":"block"}`), 플러그인 `monitors` 매니페스트 키로 세션 시작/스킬 호출 시 백그라운드 모니터 자동 구동, `EnterWorktree`에 `path` 파라미터로 기존 worktree 전환, `/proactive`=`/loop` 별칭, 정지된 API 스트림 5분 후 중단 후 non-streaming 재시도 |
| [v2.1.101](https://github.com/anthropics/claude-code/releases/tag/v2.1.101) | UX | **`/team-onboarding` & `/ultraplan`** | `/team-onboarding`으로 팀원 온보딩 가이드 자동 생성, `/ultraplan` 원격 클라우드 환경 자동 생성, OS CA 인증서 신뢰 기본 적용 (엔터프라이즈 TLS 프록시), 포커스 모드 요약 개선, 세션 제목으로 `--resume` 가능 |
| [v2.1.98](https://github.com/anthropics/claude-code/releases/tag/v2.1.98) | Platform | **Vertex AI 위저드 & PID 샌드박스** | Google Vertex AI 대화형 셋업 위저드, Linux PID namespace 서브프로세스 샌드박싱, `Monitor` 도구 추가, `CLAUDE_CODE_PERFORCE_MODE` Perforce 지원, `CLAUDE_CODE_SCRIPT_CAPS` 스크립트 호출 제한 |
| [v2.1.97](https://github.com/anthropics/claude-code/releases/tag/v2.1.97) | UX | **Focus View & NO_FLICKER 안정화** | `Ctrl+O` 포커스 뷰 토글, statusline `refreshInterval` 주기 갱신, Cedar 구문 하이라이팅, Bridge 세션에 로컬 git 정보 표시, NO_FLICKER 다수 수정 |
| [v2.1.94](https://github.com/anthropics/claude-code/releases/tag/v2.1.94) | Platform | **Bedrock Mantle 지원 & effort high 기본** | `CLAUDE_CODE_USE_MANTLE=1`로 Mantle 지원, 기본 effort medium→high 변경, Console 로그인 수정, `--resume` worktree 직접 재개 |
| [v2.1.92](https://github.com/anthropics/claude-code/releases/tag/v2.1.92) | UX | **Bedrock 셋업 위저드 & `/cost` 세부 표시** | 로그인 화면에서 Bedrock 대화형 설정 위저드, `/cost`에 모델별·캐시 히트 비용 분류, `forceRemoteSettingsRefresh` 정책, `/release-notes` 버전 선택 UI |
| [v2.1.91](https://github.com/anthropics/claude-code/releases/tag/v2.1.91) | Extensibility | **MCP 대용량 결과 & 플러그인 실행파일** | MCP 도구 결과 최대 500K까지 크기 제한 재정의, 플러그인 `bin/` 실행파일 지원, `disableSkillShellExecution` 설정 |
| [v2.1.90](https://github.com/anthropics/claude-code/releases/tag/v2.1.90) | UX | **`/powerup` 기능 튜토리얼** | 기능별 애니메이션 데모로 학습하는 `/powerup` 커맨드, auto 모드 사용자 제한 지시 반영 수정, SSE 대용량 프레임 선형 시간 처리 |
| [v2.1.89](https://github.com/anthropics/claude-code/releases/tag/v2.1.89) | Automation | **`defer` 권한 결정 & Flicker-free 렌더링** | PreToolUse hooks에 `"defer"` 결정 추가, `CLAUDE_CODE_NO_FLICKER=1` alt-screen 렌더링, `PermissionDenied` hook, auto 모드 거부 알림 및 `/permissions` Recent 탭 재시도 |
| [v2.1.86](https://github.com/anthropics/claude-code/releases/tag/v2.1.86) | Stability | **세션 안정성 & 토큰 최적화** | `--resume` 호환성 수정, Read 도구 토큰 절감 포맷, `@` 멘션 JSON 이스케이프 제거, 메모리 렌더 캐시 누수 수정 |
| [v2.1.85](https://github.com/anthropics/claude-code/releases/tag/v2.1.85) | Extensibility | **Hook 조건부 필터링 & MCP OAuth RFC 9728** | hooks에 `if` 필드로 조건부 실행, MCP OAuth RFC 9728 Protected Resource Metadata, PreToolUse hooks `AskUserQuestion` 응답 지원 |
| [v2.1.84](https://github.com/anthropics/claude-code/releases/tag/v2.1.84) | Platform | **PowerShell 도구 & IME 입력 수정** | Windows PowerShell 도구 opt-in 프리뷰, CJK IME 인라인 렌더링 수정, `TaskCreated` hook, idle-return 프롬프트(75분+), 토큰 1M+ 표기 개선 |
| [v2.1.83](https://github.com/anthropics/claude-code/releases/tag/v2.1.83) | Mgmt | **`managed-settings.d/` & 트랜스크립트 검색** | 관리 설정 drop-in 디렉토리, `CwdChanged`/`FileChanged` hook, 트랜스크립트 `/` 검색, `sandbox.failIfUnavailable`, 이미지 `[Image #N]` 칩, subagent `initialPrompt` |
| [v2.1.81](https://github.com/anthropics/claude-code/releases/tag/v2.1.81) | Automation | **`--bare` 모드 & Channels 릴레이** | 스크립팅용 `--bare` 플래그 (hooks/LSP/플러그인 생략), `--channels`로 MCP 서버가 권한 승인 프롬프트를 모바일로 전달 가능 |
| [v2.1.80](https://github.com/anthropics/claude-code/releases/tag/v2.1.80) | Extensibility | **Channels (Research Preview)** | MCP 서버가 세션에 메시지를 push할 수 있는 `--channels`, 스킬/슬래시커맨드에 `effort` frontmatter 지원, statusline에 `rate_limits` 필드 추가 |
| [v2.1.79](https://github.com/anthropics/claude-code/releases/tag/v2.1.79) | IDE | VS Code Remote Control | VS Code에서 `/remote-control`로 claude.ai/code와 브릿지 세션, AI 기반 세션 탭 타이틀 자동 생성 |
| [v2.1.78](https://github.com/anthropics/claude-code/releases/tag/v2.1.78) | Extensibility | Streaming 개선 & 플러그인 데이터 | 응답 텍스트 라인별 스트리밍, `${CLAUDE_PLUGIN_DATA}` 영구 저장소, `StopFailure` hook, tmux passthrough 알림 지원 |
| [v2.1.77](https://github.com/anthropics/claude-code/releases/tag/v2.1.77) | Performance | **출력 토큰 대폭 확대** | Opus 4.6 기본 64k, 상한 128k 토큰, `/copy N` 인덱스 지원, `/fork` → `/branch` 리네임, 세션 재개 최대 45% 빨라짐 |
| [v2.1.76](https://github.com/anthropics/claude-code/releases/tag/v2.1.76) | Integration | **MCP Elicitation** | MCP 서버가 태스크 중 사용자에게 구조화된 입력을 요청 가능 (폼/브라우저 URL), `/effort` 커맨드, `worktree.sparsePaths` 설정 |
| [v2.1.75](https://github.com/anthropics/claude-code/releases/tag/v2.1.75) | Model | **Opus 4.6 1M 컨텍스트 기본** | Max/Team/Enterprise에서 Opus 4.6 1M 컨텍스트 기본 적용, `/color` 커맨드, 메모리 파일에 last-modified 타임스탬프 |
| [v2.1.74](https://github.com/anthropics/claude-code/releases/tag/v2.1.74) | UX | `/context` 커맨드 & 메모리 설정 | `/context`로 컨텍스트 사용량 분석 및 최적화 팁 제공, `autoMemoryDirectory` 설정, 스트리밍 버퍼 메모리 누수 수정 |
| [v2.1.73](https://github.com/anthropics/claude-code/releases/tag/v2.1.73) | Stability | `modelOverrides` & 안정성 패치 | 모델 피커 항목을 커스텀 provider 모델 ID로 매핑, Bedrock/Vertex/Foundry 기본 Opus 4.6 적용, CPU 100% 프리즈 수정 |
| [v2.1.72](https://github.com/anthropics/claude-code/releases/tag/v2.1.72) | UX | Effort 단순화 & Plan 개선 | effort 레벨을 low/medium/high로 단순화 (○ ◐ ●), `/plan` 설명 인자 지원, `ExitWorktree` 도구, `/copy` 파일 쓰기(`w`키), bash 파싱 네이티브 모듈 전환, 번들 ~510KB 축소 |
| [v2.1.71](https://github.com/anthropics/claude-code/releases/tag/v2.1.71) | Automation | **`/loop` 커맨드 & Cron 스케줄링** | `/loop 5m check the deploy` 식의 반복 실행 커맨드, 세션 내 cron 스케줄링, `voice:pushToTalk` 키 리바인딩, 장시간 세션 stdin 프리즈 수정 |
| [v2.1.70](https://github.com/anthropics/claude-code/releases/tag/v2.1.70) | Stability | 서드파티 API & VS Code 안정성 | `ANTHROPIC_BASE_URL` 서드파티 게이트웨이 400 에러 수정, Windows/WSL 비ASCII 클립보드 수정, VS Code 세션 관리 아이콘·MCP 관리 다이얼로그 추가 |
| [v2.1.69](https://github.com/anthropics/claude-code/releases/tag/v2.1.69) | Skills | `/claude-api` 스킬 & 다국어 음성 | Claude API 개발용 스킬, 음성 STT 20개 언어로 추가, effort 표시 UI, `sandbox.enableWeakerNetworkIsolation`, `/reload-plugins`, 다수 메모리 누수 수정 |
| [v2.1.68](https://github.com/anthropics/claude-code/releases/tag/v2.1.68) | Model | **Opus 4.6 medium effort 기본** | Max/Team 구독자 기본 effort를 medium으로 변경, "ultrathink" 키워드 부활 (high effort), Opus 4·4.1 퇴출 → 자동 4.6 이관 |
| [v2.1.63](https://github.com/anthropics/claude-code/releases/tag/v2.1.63) | Extensibility | HTTP Hooks & 메모리 누수 다수 수정 | HTTP hooks (POST JSON) 추가, `/simplify`·`/batch` 번들 슬래시 커맨드, 프로젝트 설정/auto memory가 git worktree 간 공유, 10+ 메모리 누수 수정 |
| [v2.1.59](https://github.com/anthropics/claude-code/releases/tag/v2.1.59) | UX | **Auto Memory** & `/copy` | 유용한 컨텍스트를 자동으로 auto-memory에 저장, `/copy` 커맨드에 코드 블록 선택 UI 추가 |
| [v2.1.53](https://github.com/anthropics/claude-code/releases/tag/v2.1.53) | Stability | Windows & 크로스 플랫폼 안정성 | Windows ARM64 크래시 수정, WASM 인터프리터 크래시 수정, UI 깜빡임 수정, `ctrl+f` 일괄 에이전트 종료 개선 |
| [v2.1.51](https://github.com/anthropics/claude-code/releases/tag/v2.1.51) | Platform | Remote Control & Managed Settings | `claude remote-control` 서브커맨드, macOS plist / Windows Registry로 관리형 설정, 커스텀 npm 레지스트리 지원 |
| [v2.1.50](https://github.com/anthropics/claude-code/releases/tag/v2.1.50) | Performance | 메모리 최적화 & 1M 컨텍스트 | 장시간 세션 메모리 누수 수정, Opus 4.6 fast mode 1M 컨텍스트 윈도우, `claude agents` CLI 명령 추가 |
| [v2.1.49](https://github.com/anthropics/claude-code/releases/tag/v2.1.49) | Isolation | Git Worktree 세션 | `--worktree` (`-w`) 플래그로 격리된 git worktree 세션 지원, subagent에도 `isolation: "worktree"` 모드 추가 |
| [v2.1.47](https://github.com/anthropics/claude-code/releases/tag/v2.1.47) | Stability | 안정성 일괄 패치 | PDF 대화 compaction 수정, Windows MSYS2/Cygwin bash 수정, `chat:newline` keybinding 등 70+ 버그픽스 |
| [v2.1.46](https://github.com/anthropics/claude-code/releases/tag/v2.1.46) | Integration | claude.ai MCP 커넥터 | claude.ai의 MCP 커넥터를 Claude Code에서 사용 가능 |
| [v2.1.32](https://github.com/anthropics/claude-code/releases/tag/v2.1.32) | Multi-Agent | **Agent Teams** (Research Preview) | 다중 에이전트 협업 기능, 자동 메모리 기록/회상, "Summarize from here" 메시지 셀렉터 |
| [v2.1.18](https://github.com/anthropics/claude-code/releases/tag/v2.1.18) | UX | 커스텀 키보드 단축키 | 컨텍스트별 설정 가능한 키보드 단축키 및 chord 시퀀스 지원 |
| [v2.1.16](https://github.com/anthropics/claude-code/releases/tag/v2.1.16) | Task Mgmt | 태스크 관리 시스템 | 의존성 추적이 가능한 새로운 태스크 관리 시스템 |
| [v2.1.3](https://github.com/anthropics/claude-code/releases/tag/v2.1.3) | Skills | Slash commands + Skills 통합 | 슬래시 커맨드와 스킬을 하나로 합쳐 단순화 |
| [v2.1.2](https://github.com/anthropics/claude-code/releases/tag/v2.1.2) | Platform | Windows winget 설치 | Windows Package Manager 설치 지원, OSC 8 하이퍼링크 |
| [v2.0.72](https://github.com/anthropics/claude-code/releases/tag/v2.0.72) | Integration | **Claude in Chrome** (Beta) | Chrome 확장 프로그램 연동, `@` 멘션 3배 속도 향상 |
| [v2.0.64](https://github.com/anthropics/claude-code/releases/tag/v2.0.64) | Core | 비동기 실행 & `/stats` | Agent/bash 비동기 실행, `/stats` 통계, `/rename` 세션 이름, `.claude/rules/` 지원 |
| [v2.0.60](https://github.com/anthropics/claude-code/releases/tag/v2.0.60) | Agent | **Background Agent** | 백그라운드 에이전트 지원, `&`로 웹에 백그라운드 태스크 전송 |
| [v2.0.51](https://github.com/anthropics/claude-code/releases/tag/v2.0.51) | Product | **Claude Code for Desktop** | 데스크톱 앱 출시, Plan Mode 개선, 사용량 한도 알림 개선 |
| [v2.0.45](https://github.com/anthropics/claude-code/releases/tag/v2.0.45) | Platform | Microsoft Foundry 지원 | MS Foundry 지원, `PermissionRequest` hook, 백그라운드 태스크 `&` 전송 |
| [v2.0.28](https://github.com/anthropics/claude-code/releases/tag/v2.0.28) | Agent | Plan subagent & Subagent 재개 | Plan subagent 도입, subagent 재개 가능, 동적 모델 선택, `--max-budget-usd` 플래그 |
| [v2.0.24](https://github.com/anthropics/claude-code/releases/tag/v2.0.24) | Security | **Sandbox Mode** | Linux/Mac BashTool 샌드박스 모드 릴리스, Claude Code Web teleport 지원 |
| [v2.0.20](https://github.com/anthropics/claude-code/releases/tag/v2.0.20) | Skills | **Claude Skills** | 스킬 시스템 도입 |
| [v2.0.12](https://github.com/anthropics/claude-code/releases/tag/v2.0.12) | Extensibility | **Plugin System** | 플러그인 시스템 릴리스, `/plugin install`, marketplace, 구조 검증 |
| [v2.0.10](https://github.com/anthropics/claude-code/releases/tag/v2.0.10) | Core | 터미널 렌더러 재작성 | 새 터미널 렌더러, `Ctrl+G` 외부 에디터, PreToolUse hook 입력 수정 |
| [v2.0.0](https://github.com/anthropics/claude-code/releases/tag/v2.0.0) | **Major** | **v2.0 릴리스** | VS Code 네이티브 확장, 새 UI, `/rewind`, `/usage`, Tab 사고모드 토글, `Ctrl+R` 히스토리 검색, Agent SDK |
| [v1.0.60](https://github.com/anthropics/claude-code/releases/tag/v1.0.60) | Agent | 커스텀 Subagent | 특정 태스크용 커스텀 subagent 생성 기능 |
| [v1.0.58](https://github.com/anthropics/claude-code/releases/tag/v1.0.58) | Tool | PDF 읽기 지원 | Read 도구에서 PDF 파일 직접 읽기 가능 |
| [v1.0.51](https://github.com/anthropics/claude-code/releases/tag/v1.0.51) | Platform | **Windows 네이티브 지원** | Git for Windows 기반 네이티브 Windows 지원 |
| [v1.0.44](https://github.com/anthropics/claude-code/releases/tag/v1.0.44) | UX | `/export` & MCP 개선 | 대화 공유 `/export`, MCP 리소스 링크, `Ctrl+Z` suspend 변경 |
| [v1.0.38](https://github.com/anthropics/claude-code/releases/tag/v1.0.38) | Extensibility | **Hooks 시스템** | 커스터마이징을 위한 hooks 시스템 릴리스 |
| [v1.0.30](https://github.com/anthropics/claude-code/releases/tag/v1.0.30) | Skills | 커스텀 슬래시 커맨드 | bash 실행, `@`-mention, thinking 지원 커스텀 슬래시 커맨드 |

---

## 주요 키보드 단축키 변경 이력

| 버전 | 변경 내용 |
|------|----------|
| v2.1.110 | `Ctrl+O`를 normal/verbose transcript 토글 전용으로 변경, 포커스 뷰는 `/focus` 커맨드로 분리 |
| v2.1.108 | `/undo`가 `/rewind` 별칭으로 추가, `/resume` 피커가 현재 디렉토리 세션 기본 노출·`Ctrl+A`로 전체 프로젝트 |
| v2.1.105 | `/proactive`가 `/loop` 별칭으로 추가, `Ctrl+J` 줄바꿈 미동작 수정, alt+enter ESC-prefix 인코딩 터미널 줄바꿈 수정 |
| v2.1.101 | `Ctrl+]`, `Ctrl+\`, `Ctrl+^` 일부 터미널 미작동 수정 |
| v2.1.97 | `Ctrl+O`: NO_FLICKER 모드 포커스 뷰 토글 (프롬프트·도구 요약·최종 응답만 표시) |
| v2.1.92 | `/tag` 및 `/vim` 커맨드 제거, `/release-notes` 버전 선택 UI |
| v2.1.89 | auto 모드 거부 명령 `/permissions` Recent 탭 표시, `r`키 재시도 |
| v2.1.84 | `Ctrl+X Ctrl+E`: 외부 에디터 열기 별칭 (readline 네이티브), `chat:killAgents`/`chat:fastMode` 리바인딩 가능 |
| v2.1.83 | 트랜스크립트 모드에서 `/` 검색, `n`/`N` 탐색, 백그라운드 에이전트 종료 `Ctrl+F` → `Ctrl+X Ctrl+K`로 변경 |
| v2.1.78 | `Ctrl+U`: normal 모드에서 readline kill-line으로 변경 (반페이지 스크롤은 transcript 모드 전용) |
| v2.1.77 | `/copy N`: N번째 최신 어시스턴트 응답 복사, `/fork` → `/branch` 리네임 |
| v2.1.71 | `voice:pushToTalk` 키바인딩 리바인딩 가능 (기본값: Space) |
| v2.1.69 | `Ctrl+U`: 빈 bash 프롬프트에서 bash 모드 종료, 숫자 키패드 지원 |
| v2.1.49 | `Ctrl+F`: 백그라운드 에이전트 종료 (2회 눌러 확인) |
| v2.1.18 | 커스텀 키보드 단축키 시스템 도입 |
| v2.0.72 | 사고 모드 토글: `Tab` → `Alt+T` |
| v2.0.65 | `Alt+P`: 프롬프트 작성 중 모델 전환 |
| v2.0.0 | `Ctrl+R`: 히스토리 검색, `Tab`: 사고모드 토글 |
| v1.0.71 | `Ctrl+B`: bash 백그라운드 실행 |
| v1.0.48 | Vim `c`, `f/F`, `t/T` 모션 추가 |
| v1.0.44 | `Ctrl+Z`: suspend로 변경 (undo는 `Ctrl+U`) |
| v1.0.30 | `Ctrl+R`: 타임스탬프 및 `Ctrl+C` 핸들링 |

---

## 플랫폼 & 인프라 지원 확대

| 버전 | 플랫폼 | 내용 |
|------|--------|------|
| v2.1.110 | Perf | MCP SSE/HTTP 응답 중 연결 드롭 시 무한 대기 수정, non-streaming 폴백 재시도 multi-minute 행 수정, 텍스트 선택 중 도구 실행 시 fullscreen CPU 과부하 수정, 동기화 출력 미지원 터미널(Terminal.app 등) 시작 렌더링 수정 |
| v2.1.108 | Perf | 파일 읽기·편집·구문 강조 메모리 풋프린트 축소 (language grammar on-demand 로딩), `ENABLE_PROMPT_CACHING_1H`로 1시간 캐시 TTL 옵트인, `DISABLE_TELEMETRY` 구독자 5분 fallback 수정 |
| v2.1.105 | Perf | 정지된 API 스트림 5분 무응답 후 중단·non-streaming 재시도, 긴 단일 라인 파일 쓰기 UI truncate, 네트워크 에러 즉시 재시도 메시지 표시 |
| v2.1.105 | Terminal | SSH/mosh 상 Ghostty/Kitty/Alacritty/WezTerm/foot/rio/Contour 16색 팔레트 수정, `rich`/`loguru` 클릭 링크 bash 출력 수정, ASCII art 리딩 공백 보존 |
| v2.1.101 | Perf | 장시간 세션 가상 스크롤러 메모리 누수 수정, 대형 세션 `--resume`/`--continue` 컨텍스트 유실 수정, 하드코딩 5분 타임아웃 제거 |
| v2.1.101 | Platform | OS CA 인증서 스토어 기본 신뢰 (엔터프라이즈 TLS 프록시), Bedrock SigV4 403 인증 오류 수정 |
| v2.1.98 | Security | Linux PID namespace 서브프로세스 격리, 백슬래시 이스케이프 Bash 권한 우회 수정, 복합 명령 강제 프롬프트 우회 수정 |
| v2.1.98 | Platform | Google Vertex AI 대화형 셋업 위저드, Perforce `p4 edit` 모드, kitty 키보드 프로토콜 대문자 소문자 변환 수정 |
| v2.1.97 | Perf | MCP HTTP/SSE 재연결 시 ~50MB/hr 버퍼 누수 수정, 429 재시도 지수 백오프 최소값 적용, 세션 트랜스크립트 크기 최적화 |
| v2.1.94 | Platform | Amazon Bedrock Mantle 지원 (`CLAUDE_CODE_USE_MANTLE=1`), CJK UTF-8 스트림 깨짐 수정 |
| v2.1.92 | Perf | Write 도구 diff 대형 파일 60% 속도 향상, Linux sandbox `apply-seccomp` 헬퍼 npm/native 빌드 모두 포함 |
| v2.1.91 | Perf | Edit 도구 shorter `old_string` 앵커로 출력 토큰 절감 |
| v2.1.90 | Perf | WASM yoga-layout → 순수 TypeScript 구현 전환, `/powerup` 기능 튜토리얼 |
| v2.1.89 | Perf | autocompact 무한 루프 수정, 중첩 CLAUDE.md 중복 주입 방지, Bash 도구 포맷터/린터 파일 변경 감지 경고 |
| v2.1.86 | Perf | Read 도구 토큰 사용량 절감 포맷, `@` 멘션 JSON 이스케이프 제거 |
| v2.1.85 | MCP | MCP OAuth RFC 9728 Protected Resource Metadata discovery |
| v2.1.84 | Platform | PowerShell 도구 opt-in 프리뷰, CJK IME 인라인 수정, Scalar/GVFS partial clone 대량 blob 다운로드 수정 |
| v2.1.83 | Mgmt | `managed-settings.d/` drop-in 디렉토리, `sandbox.failIfUnavailable`, `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB` 자격 증명 제거 |
| v2.1.81 | MCP | MCP OAuth Client ID Metadata Document (CIMD / SEP-991) 지원 |
| v2.1.80 | Perf | 대형 저장소(250k 파일) 시작 시 메모리 ~80MB 절감 |
| v2.1.79 | VS Code | `/remote-control` 브릿지, AI 세션 타이틀, 시작 메모리 ~18MB 절감 |
| v2.1.78 | Terminal | tmux passthrough 알림 지원 (iTerm2/Kitty/Ghostty), 라인별 응답 스트리밍 |
| v2.1.77 | Performance | macOS 시작 ~60ms 단축, `--resume` 최대 45% 빨라짐·~100-150MB 메모리 절감 |
| v2.1.76 | MCP | MCP Elicitation — 서버가 태스크 중 구조화된 입력 요청 가능 |
| v2.1.75 | Managed | Windows managed settings 경로 변경: `C:\Program Files\ClaudeCode\managed-settings.json` |
| v2.1.74 | Platform | RTL 텍스트(히브리어, 아랍어) Windows Terminal/VS Code 렌더링 수정, macOS 마이크 권한 entitlement 추가 |
| v2.1.73 | Platform | Amazon Linux 2 (glibc 2.26) 네이티브 모듈 지원, Bedrock/Vertex/Foundry 기본 Opus 4.6 |
| v2.1.72 | VS Code | `vscode://anthropic.claude-code/open` URI 핸들러 추가, effort 표시 인디케이터 |
| v2.1.70 | VS Code | 세션 관리 아이콘, Plan 마크다운 뷰, 네이티브 MCP 서버 관리 다이얼로그 |
| v2.1.69 | Voice | 음성 STT 20개 언어 지원 (러시아어, 폴란드어, 터키어, 네덜란드어 등 10개 추가) |
| v2.1.51 | Mgmt | macOS plist / Windows Registry 관리형 설정 |
| v2.1.41 | ARM64 | Windows ARM64 네이티브 바이너리 |
| v2.1.2 | Windows | winget 패키지 매니저 설치 |
| v2.0.45 | Cloud | Microsoft Foundry 지원 |
| v2.0.0 | IDE | VS Code 네이티브 확장 |
| v1.0.73 | Linux | Alpine, musl 지원 |
| v1.0.51 | Windows | 네이티브 Windows 지원 (Git for Windows) |
| v1.0.35 | MCP | OAuth Authorization Server discovery |

---

## SDK / API 주요 변경

| 버전 | 변경 내용 |
|------|----------|
| v2.1.110 | `/tui` 커맨드 및 `tui` 설정, 모바일 push notification 도구, `autoScrollEnabled` 설정, `Ctrl+G` 외부 에디터에 Claude 마지막 응답을 주석 컨텍스트로 포함 옵션, SDK/headless 세션 `TRACEPARENT`/`TRACESTATE` 환경변수 읽기, `--resume`/`--continue`로 미만료 스케줄 태스크 부활, Bash 도구 문서화된 최대 timeout 강제 |
| v2.1.108 | `ENABLE_PROMPT_CACHING_1H` (1시간 프롬프트 캐시 TTL), `FORCE_PROMPT_CACHING_5M`, `/recap` (세션 복귀 컨텍스트), `CLAUDE_CODE_ENABLE_AWAY_SUMMARY`로 텔레메트리 비활성화 시 강제, 모델이 Skill 도구로 `/init`·`/review`·`/security-review` 호출 가능, `/undo`=`/rewind` 별칭, `/model` 중간 전환 경고 (캐시 무효화 이유), prompt caching 비활성 시 시작 경고 |
| v2.1.105 | `EnterWorktree` `path` 파라미터, PreCompact hook `{"decision":"block"}` compaction 차단, 플러그인 `monitors` 매니페스트 키 (세션 시작/스킬 호출 자동 구동), `/proactive`=`/loop` 별칭, MCP 대용량 truncation 포맷별 레시피 (`jq` JSON, Read chunk 크기 계산), 스킬 description 250→1536자 확장, stale agent worktree squash-merge 정리 |
| v2.1.101 | `/team-onboarding` 팀원 온보딩 가이드 생성, `/ultraplan` 원격 환경 자동 생성, `--resume <name>` 세션 타이틀 지원, brief 모드 재시도 개선, SDK `query()` subprocess/temp 파일 break/await 정리, OTEL `OTEL_LOG_USER_PROMPTS`/`OTEL_LOG_TOOL_DETAILS`/`OTEL_LOG_TOOL_CONTENT` 지원 |
| v2.1.98 | `Monitor` 도구 (백그라운드 스크립트 이벤트 스트리밍), `CLAUDE_CODE_PERFORCE_MODE`, `CLAUDE_CODE_SCRIPT_CAPS`, `--exclude-dynamic-system-prompt-sections` 크로스유저 캐싱, LSP `clientInfo` 식별, W3C `TRACEPARENT` Bash 전파 |
| v2.1.97 | statusline `refreshInterval` 주기 갱신, `workspace.git_worktree` statusline 입력, `sandbox.network.allowMachLookup` macOS 적용, Bash OTEL `TRACEPARENT` 환경변수 전파, `/claude-api` 스킬에 Managed Agents 추가 |
| v2.1.94 | `CLAUDE_CODE_USE_MANTLE=1` Bedrock Mantle 지원, `keep-coding-instructions` frontmatter, `hookSpecificOutput.sessionTitle` (UserPromptSubmit), 플러그인 스킬 frontmatter `name` 기반 호출명 |
| v2.1.92 | `forceRemoteSettingsRefresh` 정책 (fail-closed), `/cost` 모델별·캐시 히트 분류, Bedrock 대화형 셋업 위저드 |
| v2.1.91 | MCP `_meta["anthropic/maxResultSizeChars"]` (최대 500K), `disableSkillShellExecution` 설정, 플러그인 `bin/` 실행파일 |
| v2.1.90 | SSE 대용량 프레임 선형 시간 처리, SDK 대화 transcript 이차 시간 → 선형 최적화 |
| v2.1.89 | PreToolUse `"defer"` 결정, `PermissionDenied` hook, `CLAUDE_CODE_NO_FLICKER=1`, `MCP_CONNECTION_NONBLOCKING`, Edit symlink 대상 체크, hook `if` 복합 명령 매칭 수정 |
| v2.1.86 | `.jj`/`.sl` VCS 디렉토리 제외, Read 도구 compact 라인 넘버 포맷, `@` 멘션 토큰 오버헤드 절감 |
| v2.1.85 | hooks `if` 조건부 필터 (permission rule 문법), PreToolUse `updatedInput`으로 `AskUserQuestion` 자동 응답, `OTEL_LOG_TOOL_DETAILS=1` |
| v2.1.84 | PowerShell 도구 (Windows opt-in), `TaskCreated` hook, `CLAUDE_STREAM_IDLE_TIMEOUT_MS`, `allowedChannelPlugins` 관리 설정, MCP 설명 2KB 제한, idle-return 프롬프트 |
| v2.1.83 | `managed-settings.d/` drop-in, `CwdChanged`/`FileChanged` hook, `sandbox.failIfUnavailable`, `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB`, subagent `initialPrompt`, `TaskOutput` → `Read` 전환 |
| v2.1.81 | `--bare` 플래그 (hooks/LSP/플러그인 생략), `--channels` 권한 릴레이 |
| v2.1.80 | `--channels` (Research Preview), statusline `rate_limits` 필드, 스킬/커맨드 `effort` frontmatter |
| v2.1.79 | `--console` 플래그 (Anthropic Console API 인증), `CLAUDE_CODE_PLUGIN_SEED_DIR` 다중 경로 지원 |
| v2.1.78 | `StopFailure` hook, `${CLAUDE_PLUGIN_DATA}` 영구 저장소, `ANTHROPIC_CUSTOM_MODEL_OPTION` 환경변수, Agent 도구에서 `resume` 파라미터 제거 → `SendMessage` 사용 |
| v2.1.77 | Opus 4.6 기본 출력 64k / 상한 128k 토큰, `allowRead` 샌드박스 설정 |
| v2.1.76 | `Elicitation`·`ElicitationResult` hooks, `PostCompact` hook, `-n`/`--name` 세션명 플래그, `worktree.sparsePaths`, `/effort` 커맨드 |
| v2.1.74 | `autoMemoryDirectory` 설정, `SessionEnd` hook timeout `CLAUDE_CODE_SESSIONEND_HOOKS_TIMEOUT_MS`로 설정 가능 |
| v2.1.73 | `modelOverrides` 설정 (모델 피커 → 커스텀 provider ID 매핑) |
| v2.1.72 | `CLAUDE_CODE_DISABLE_CRON` 환경변수, Agent 도구에 `model` 파라미터 복원, SDK `query()` 프롬프트 캐시 무효화 수정 (토큰 비용 최대 12배 절감) |
| v2.1.69 | `InstructionsLoaded` hook 이벤트, hook 이벤트에 `agent_id`·`agent_type`·`worktree` 필드 추가, `${CLAUDE_SKILL_DIR}` 변수 |
| v2.1.63 | `ENABLE_CLAUDEAI_MCP_SERVERS` 환경변수로 claude.ai MCP 서버 옵트아웃 지원 |
| v2.1.51 | `CLAUDE_CODE_ACCOUNT_UUID`, `CLAUDE_CODE_USER_EMAIL`, `CLAUDE_CODE_ORGANIZATION_UUID` 환경변수 추가 |
| v2.1.49 | SDK model info에 `supportsEffort`, `supportedEffortLevels`, `supportsAdaptiveThinking` 추가 |
| v2.1.33 | `Task(agent_type)` 구문으로 sub-agent 제한, `memory` frontmatter |
| v2.0.28 | `--max-budget-usd` 플래그 추가 |
| v2.0.0 | Claude Agent SDK로 리브랜딩, `--agents` 플래그 |
| v1.0.82 | 요청 취소, `additionalDirectories` 옵션 |
| v1.0.59 | 도구 확인(tool confirmation) 지원 |

---

## 보안 관련 주요 패치

| 버전 | 내용 |
|------|------|
| v2.1.110 | "Open in editor" 액션에서 신뢰되지 않은 파일명 기반 커맨드 인젝션 방지 강화, `PermissionRequest` hooks의 `updatedInput`이 `permissions.deny`에 재검증되지 않던 버그 수정, `setMode:'bypassPermissions'` 업데이트가 `disableBypassPermissionsMode` 정책 준수 |
| v2.1.101 | POSIX `which` 폴백 LSP 바이너리 탐지 커맨드 인젝션 취약점 수정, `permissions.deny` 규칙이 PreToolUse hook `permissionDecision: "ask"` 우회하는 버그 수정, 서브에이전트 worktree 격리 시 Read/Edit 접근 거부 수정 |
| v2.1.98 | 백슬래시 이스케이프 플래그 Bash 권한 우회 수정, 복합 Bash 명령 강제 프롬프트 우회 수정, `/dev/tcp`·`/dev/udp` 리다이렉트 프롬프트 미표시 수정, env-var 접두사 읽기 전용 명령 권한 수정, `grep -f`/`rg -f` 외부 패턴 파일 프롬프트 미표시 수정, Linux PID namespace 서브프로세스 샌드박싱 |
| v2.1.97 | `--dangerously-skip-permissions` protected path 승인 후 accept-edits 강등 수정, Bash 도구 env-var 접두사·네트워크 리다이렉트 권한 강화, managed-settings allow 규칙 삭제 후 재시작 전까지 활성 유지 버그 수정, `permissions.additionalDirectories` 세션 중 변경 미적용 수정 |
| v2.1.92 | Linux sandbox `apply-seccomp` 헬퍼 npm/native 빌드 모두 포함 |
| v2.1.90 | `.husky` 보호 디렉토리 추가 (acceptEdits 모드) |
| v2.1.89 | Edit/Read symlink 대상 경로 검증, auto 모드 사용자 제한 지시("don't push" 등) 반영 수정, autocompact 무한 루프 방지 |
| v2.1.86 | 공식 마켓플레이스 플러그인 스크립트 macOS/Linux "Permission denied" 수정 (v2.1.83 회귀) |
| v2.1.85 | `deniedMcpServers` 설정이 claude.ai MCP 서버 차단하지 않는 버그 수정 |
| v2.1.84 | `--mcp-config` CLI 플래그가 `allowedMcpServers`/`deniedMcpServers` 관리 정책 우회하는 취약점 수정, Partial clone 대량 blob 다운로드 방지 |
| v2.1.83 | `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB=1`로 하위 프로세스에서 Anthropic/클라우드 자격 증명 제거 |
| v2.1.78 | 샌드박스 의존성 누락 시 자동 비활성화 대신 경고 표시, `bypassPermissions` 모드에서 `.git`/`.claude` 등 보호 디렉토리 쓰기 권한 수정 |
| v2.1.77 | PreToolUse hooks의 `"allow"` 반환이 `deny` 권한 규칙 우회하는 취약점 수정 (Enterprise managed settings 포함) |
| v2.1.74 | managed policy `ask` 규칙이 user `allow` 또는 skill `allowed-tools`에 의해 우회되는 취약점 수정 |
| v2.1.69 | gitignore 디렉토리에서 중첩 스킬 탐색 차단, `.mcp.json` 서버 자동 활성화 trust 다이얼로그 수정, symlink bypass 보안 수정 |
| v2.1.51 | `statusLine`·`fileSuggestion` hooks가 workspace trust 없이 실행되는 취약점 수정 |
| v2.1.38 | heredoc delimiter 파싱 보완 (command smuggling 방지) |
| v2.1.34 | bash permission bypass 취약점 수정 |
| v2.1.7 | wildcard permission rules 보안 취약점 수정 |
| v2.1.6 | shell line continuation을 통한 permission bypass 수정 |
| v2.1.2 | bash 처리 시 command injection 취약점 수정 |
| v2.0.24 | BashTool 샌드박스 모드 릴리스 |
| v1.0.124 | Bash tool permission check 보안 취약점 수정 |
| v1.0.120 | Bash permission check 보안 취약점 수정 |

---

> 이 페이지는 [Claude Code CHANGELOG](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)를 기반으로 주요 변경사항만 발췌하여 정리한 것입니다. 전체 내용은 원본을 참고하세요.
