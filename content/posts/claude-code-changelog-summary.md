---
title: "Claude Code 업데이트 핵심 정리 (v1.0 ~ v2.1.81)"
date: 2026-03-22
draft: false
tags: ["Claude Code", "Anthropic", "AI", "CLI", "Changelog"]
summary: "Claude Code의 주요 업데이트를 버전별로 핵심만 추려 정리합니다. 모델 업그레이드, 신규 기능, 플랫폼 지원 등 메이저 변경사항을 한눈에 볼 수 있습니다. (v2.1.81 기준)"
---

> 원본: [anthropics/claude-code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
>
> 마지막 업데이트: 2026-03-22 (v2.1.81 기준)

---

## 모델 업그레이드 이력

| 버전 | 모델 변경 |
|------|----------|
| [v2.1.77](https://github.com/anthropics/claude-code/releases/tag/v2.1.77) | Opus 4.6 기본 최대 출력 64k 토큰, Opus 4.6·Sonnet 4.6 상한 128k 토큰으로 확대 |
| [v2.1.75](https://github.com/anthropics/claude-code/releases/tag/v2.1.75) | Opus 4.6 **1M 컨텍스트 윈도우 기본 적용** (Max/Team/Enterprise) |
| [v2.1.73](https://github.com/anthropics/claude-code/releases/tag/v2.1.73) | Bedrock/Vertex/Foundry 기본 Opus를 4.6으로 변경 (기존 4.1) |
| [v2.1.68](https://github.com/anthropics/claude-code/releases/tag/v2.1.68) | Opus 4.6 기본 effort를 medium으로 변경 (Max/Team), Opus 4·4.1 퇴출 |
| [v2.1.45](https://github.com/anthropics/claude-code/releases/tag/v2.1.45) | Claude Sonnet 4.6 지원 |
| [v2.1.36](https://github.com/anthropics/claude-code/releases/tag/v2.1.36) | Opus 4.6 Fast mode 지원 |
| [v2.1.32](https://github.com/anthropics/claude-code/releases/tag/v2.1.32) | **Claude Opus 4.6** 출시 |
| [v2.0.51](https://github.com/anthropics/claude-code/releases/tag/v2.0.51) | **Opus 4.5** 출시, Pro 사용자 extra usage로 접근 가능 |
| [v2.0.17](https://github.com/anthropics/claude-code/releases/tag/v2.0.17) | Haiku 4.5 모델 셀렉터 추가, Explore subagent에 Haiku 적용 |
| [v1.0.69](https://github.com/anthropics/claude-code/releases/tag/v1.0.69) | Opus 4.1로 업그레이드 |

---

## Major Feature 릴리스

| 버전 | 카테고리 | 핵심 기능 | 설명 |
|------|---------|----------|------|
| [v2.1.81](https://github.com/anthropics/claude-code/releases/tag/v2.1.81) | Automation | **`--bare` 모드 & Channels 릴레이** | 스크립팅용 `--bare` 플래그 (hooks/LSP/플러그인 생략), `--channels`로 MCP 서버가 권한 승인 프롬프트를 모바일로 전달 가능 |
| [v2.1.80](https://github.com/anthropics/claude-code/releases/tag/v2.1.80) | Extensibility | **Channels (Research Preview)** | MCP 서버가 세션에 메시지를 push할 수 있는 `--channels`, 스킬/슬래시커맨드에 `effort` frontmatter 지원, statusline에 `rate_limits` 필드 추가 |
| [v2.1.79](https://github.com/anthropics/claude-code/releases/tag/v2.1.79) | IDE | VS Code Remote Control | VS Code에서 `/remote-control`로 claude.ai/code와 브릿지 세션, AI 기반 세션 탭 타이틀 자동 생성 |
| [v2.1.78](https://github.com/anthropics/claude-code/releases/tag/v2.1.78) | Extensibility | Streaming 강화 & 플러그인 데이터 | 응답 텍스트 라인별 스트리밍, `${CLAUDE_PLUGIN_DATA}` 영구 저장소, `StopFailure` hook, tmux passthrough 알림 지원 |
| [v2.1.77](https://github.com/anthropics/claude-code/releases/tag/v2.1.77) | Performance | **출력 토큰 대폭 확대** | Opus 4.6 기본 64k, 상한 128k 토큰, `/copy N` 인덱스 지원, `/fork` → `/branch` 리네임, 세션 재개 최대 45% 빨라짐 |
| [v2.1.76](https://github.com/anthropics/claude-code/releases/tag/v2.1.76) | Integration | **MCP Elicitation** | MCP 서버가 태스크 중 사용자에게 구조화된 입력을 요청 가능 (폼/브라우저 URL), `/effort` 커맨드, `worktree.sparsePaths` 설정 |
| [v2.1.75](https://github.com/anthropics/claude-code/releases/tag/v2.1.75) | Model | **Opus 4.6 1M 컨텍스트 기본** | Max/Team/Enterprise에서 Opus 4.6 1M 컨텍스트 기본 적용, `/color` 커맨드, 메모리 파일에 last-modified 타임스탬프 |
| [v2.1.74](https://github.com/anthropics/claude-code/releases/tag/v2.1.74) | UX | `/context` 커맨드 & 메모리 설정 | `/context`로 컨텍스트 사용량 분석 및 최적화 팁 제공, `autoMemoryDirectory` 설정, 스트리밍 버퍼 메모리 누수 수정 |
| [v2.1.73](https://github.com/anthropics/claude-code/releases/tag/v2.1.73) | Stability | `modelOverrides` & 안정성 패치 | 모델 피커 항목을 커스텀 provider 모델 ID로 매핑, Bedrock/Vertex/Foundry 기본 Opus 4.6 적용, CPU 100% 프리즈 수정 |
| [v2.1.72](https://github.com/anthropics/claude-code/releases/tag/v2.1.72) | UX | Effort 단순화 & Plan 강화 | effort 레벨을 low/medium/high로 단순화 (○ ◐ ●), `/plan` 설명 인자 지원, `ExitWorktree` 도구, `/copy` 파일 쓰기(`w`키), bash 파싱 네이티브 모듈 전환, 번들 ~510KB 축소 |
| [v2.1.71](https://github.com/anthropics/claude-code/releases/tag/v2.1.71) | Automation | **`/loop` 커맨드 & Cron 스케줄링** | `/loop 5m check the deploy` 식의 반복 실행 커맨드, 세션 내 cron 스케줄링, `voice:pushToTalk` 키 리바인딩, 장시간 세션 stdin 프리즈 수정 |
| [v2.1.70](https://github.com/anthropics/claude-code/releases/tag/v2.1.70) | Stability | 서드파티 API & VS Code 안정성 | `ANTHROPIC_BASE_URL` 서드파티 게이트웨이 400 에러 수정, Windows/WSL 비ASCII 클립보드 수정, VS Code 세션 관리 아이콘·MCP 관리 다이얼로그 추가 |
| [v2.1.69](https://github.com/anthropics/claude-code/releases/tag/v2.1.69) | Skills | `/claude-api` 스킬 & 다국어 음성 | Claude API 개발용 스킬, 음성 STT 20개 언어 확대, effort 표시 UI, `sandbox.enableWeakerNetworkIsolation`, `/reload-plugins`, 대규모 메모리 누수 수정 |
| [v2.1.68](https://github.com/anthropics/claude-code/releases/tag/v2.1.68) | Model | **Opus 4.6 medium effort 기본** | Max/Team 구독자 기본 effort를 medium으로 변경, "ultrathink" 키워드 부활 (high effort), Opus 4·4.1 퇴출 → 자동 4.6 이관 |
| [v2.1.63](https://github.com/anthropics/claude-code/releases/tag/v2.1.63) | Extensibility | HTTP Hooks & 메모리 누수 대규모 수정 | HTTP hooks (POST JSON) 추가, `/simplify`·`/batch` 번들 슬래시 커맨드, 프로젝트 설정/auto memory가 git worktree 간 공유, 10+ 메모리 누수 수정 |
| [v2.1.59](https://github.com/anthropics/claude-code/releases/tag/v2.1.59) | UX | **Auto Memory** & `/copy` | 유용한 컨텍스트를 자동으로 auto-memory에 저장, `/copy` 커맨드에 인터랙티브 코드 블록 피커 추가 |
| [v2.1.53](https://github.com/anthropics/claude-code/releases/tag/v2.1.53) | Stability | Windows & 크로스 플랫폼 안정성 | Windows ARM64 크래시 수정, WASM 인터프리터 크래시 수정, UI 깜빡임 수정, `ctrl+f` 일괄 에이전트 종료 개선 |
| [v2.1.51](https://github.com/anthropics/claude-code/releases/tag/v2.1.51) | Platform | Remote Control & Managed Settings | `claude remote-control` 서브커맨드, macOS plist / Windows Registry로 관리형 설정, 커스텀 npm 레지스트리 지원 |
| [v2.1.50](https://github.com/anthropics/claude-code/releases/tag/v2.1.50) | Performance | 메모리 최적화 & 1M 컨텍스트 | 장시간 세션 메모리 누수 수정, Opus 4.6 fast mode 1M 컨텍스트 윈도우, `claude agents` CLI 명령 추가 |
| [v2.1.49](https://github.com/anthropics/claude-code/releases/tag/v2.1.49) | Isolation | Git Worktree 세션 | `--worktree` (`-w`) 플래그로 격리된 git worktree 세션 지원, subagent에도 `isolation: "worktree"` 모드 추가 |
| [v2.1.47](https://github.com/anthropics/claude-code/releases/tag/v2.1.47) | Stability | 대규모 안정성 패치 | PDF 대화 compaction 수정, Windows MSYS2/Cygwin bash 수정, `chat:newline` keybinding 등 70+ 버그픽스 |
| [v2.1.46](https://github.com/anthropics/claude-code/releases/tag/v2.1.46) | Integration | claude.ai MCP 커넥터 | claude.ai의 MCP 커넥터를 Claude Code에서 사용 가능 |
| [v2.1.32](https://github.com/anthropics/claude-code/releases/tag/v2.1.32) | Multi-Agent | **Agent Teams** (Research Preview) | 다중 에이전트 협업 기능, 자동 메모리 기록/회상, "Summarize from here" 메시지 셀렉터 |
| [v2.1.18](https://github.com/anthropics/claude-code/releases/tag/v2.1.18) | UX | 커스텀 키보드 단축키 | 컨텍스트별 설정 가능한 키보드 단축키 및 chord 시퀀스 지원 |
| [v2.1.16](https://github.com/anthropics/claude-code/releases/tag/v2.1.16) | Task Mgmt | 태스크 관리 시스템 | 의존성 추적이 가능한 새로운 태스크 관리 시스템 |
| [v2.1.3](https://github.com/anthropics/claude-code/releases/tag/v2.1.3) | Skills | Slash commands + Skills 통합 | 슬래시 커맨드와 스킬을 하나로 합쳐 단순화 |
| [v2.1.2](https://github.com/anthropics/claude-code/releases/tag/v2.1.2) | Platform | Windows winget 설치 | Windows Package Manager 설치 지원, OSC 8 하이퍼링크 |
| [v2.0.72](https://github.com/anthropics/claude-code/releases/tag/v2.0.72) | Integration | **Claude in Chrome** (Beta) | Chrome 확장 프로그램 연동, `@` 멘션 3배 속도 향상 |
| [v2.0.64](https://github.com/anthropics/claude-code/releases/tag/v2.0.64) | Core | 비동기 실행 & `/stats` | Agent/bash 비동기 실행, `/stats` 통계, `/rename` 세션 이름, `.claude/rules/` 지원 |
| [v2.0.60](https://github.com/anthropics/claude-code/releases/tag/v2.0.60) | Agent | **Background Agent** | 백그라운드 에이전트 지원, `&`로 웹에 백그라운드 태스크 전송 |
| [v2.0.51](https://github.com/anthropics/claude-code/releases/tag/v2.0.51) | Product | **Claude Code for Desktop** | 데스크톱 앱 출시, Plan Mode 강화, 사용량 한도 알림 개선 |
| [v2.0.45](https://github.com/anthropics/claude-code/releases/tag/v2.0.45) | Platform | Microsoft Foundry 지원 | MS Foundry 지원, `PermissionRequest` hook, 백그라운드 태스크 `&` 전송 |
| [v2.0.28](https://github.com/anthropics/claude-code/releases/tag/v2.0.28) | Agent | Plan subagent & Subagent 재개 | Plan subagent 도입, subagent 재개 가능, 동적 모델 선택, `--max-budget-usd` 플래그 |
| [v2.0.24](https://github.com/anthropics/claude-code/releases/tag/v2.0.24) | Security | **Sandbox Mode** | Linux/Mac BashTool 샌드박스 모드 릴리스, Claude Code Web teleport 지원 |
| [v2.0.20](https://github.com/anthropics/claude-code/releases/tag/v2.0.20) | Skills | **Claude Skills** | 스킬 시스템 도입 |
| [v2.0.12](https://github.com/anthropics/claude-code/releases/tag/v2.0.12) | Extensibility | **Plugin System** | 플러그인 시스템 릴리스, `/plugin install`, marketplace, 구조 검증 |
| [v2.0.10](https://github.com/anthropics/claude-code/releases/tag/v2.0.10) | Core | 터미널 렌더러 재작성 | 새 터미널 렌더러, `Ctrl+G` 외부 에디터, PreToolUse hook 입력 수정 |
| [v2.0.0](https://github.com/anthropics/claude-code/releases/tag/v2.0.0) | **Major** | **v2.0 릴리스** | VS Code 네이티브 확장, 새 UI, `/rewind`, `/usage`, Tab 사고모드 토글, `Ctrl+R` 히스토리 검색, Agent SDK |
| [v1.0.60](https://github.com/anthropics/claude-code/releases/tag/v1.0.60) | Agent | 커스텀 Subagent | 특화된 태스크를 위한 커스텀 subagent 생성 기능 |
| [v1.0.58](https://github.com/anthropics/claude-code/releases/tag/v1.0.58) | Tool | PDF 읽기 지원 | Read 도구에서 PDF 파일 직접 읽기 가능 |
| [v1.0.51](https://github.com/anthropics/claude-code/releases/tag/v1.0.51) | Platform | **Windows 네이티브 지원** | Git for Windows 기반 네이티브 Windows 지원 |
| [v1.0.44](https://github.com/anthropics/claude-code/releases/tag/v1.0.44) | UX | `/export` & MCP 개선 | 대화 공유 `/export`, MCP 리소스 링크, `Ctrl+Z` suspend 변경 |
| [v1.0.38](https://github.com/anthropics/claude-code/releases/tag/v1.0.38) | Extensibility | **Hooks 시스템** | 커스터마이징을 위한 hooks 시스템 릴리스 |
| [v1.0.30](https://github.com/anthropics/claude-code/releases/tag/v1.0.30) | Skills | 커스텀 슬래시 커맨드 | bash 실행, `@`-mention, thinking 활성화가 가능한 커스텀 슬래시 커맨드 |

---

## 주요 키보드 단축키 변경 이력

| 버전 | 변경 내용 |
|------|----------|
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
| v2.1.81 | MCP | MCP OAuth Client ID Metadata Document (CIMD / SEP-991) 지원 |
| v2.1.80 | Perf | 대규모 저장소(250k 파일) 시작 시 메모리 ~80MB 절감 |
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
| v2.1.78 | 샌드박스 의존성 누락 시 자동 비활성화 대신 경고 표시, `bypassPermissions` 모드에서 `.git`/`.claude` 등 보호 디렉토리 쓰기 권한 수정 |
| v2.1.77 | PreToolUse hooks의 `"allow"` 반환이 `deny` 권한 규칙 우회하는 취약점 수정 (Enterprise managed settings 포함) |
| v2.1.74 | managed policy `ask` 규칙이 user `allow` 또는 skill `allowed-tools`에 의해 우회되는 취약점 수정 |
| v2.1.69 | gitignore 디렉토리에서 중첩 스킬 탐색 차단, `.mcp.json` 서버 자동 활성화 trust 다이얼로그 수정, symlink bypass 보안 수정 |
| v2.1.51 | `statusLine`·`fileSuggestion` hooks가 workspace trust 없이 실행되는 취약점 수정 |
| v2.1.38 | heredoc delimiter 파싱 강화 (command smuggling 방지) |
| v2.1.34 | bash permission bypass 취약점 수정 |
| v2.1.7 | wildcard permission rules 보안 취약점 수정 |
| v2.1.6 | shell line continuation을 통한 permission bypass 수정 |
| v2.1.2 | bash 처리 시 command injection 취약점 수정 |
| v2.0.24 | BashTool 샌드박스 모드 릴리스 |
| v1.0.124 | Bash tool permission check 보안 취약점 수정 |
| v1.0.120 | Bash permission check 보안 취약점 수정 |

---

> 이 페이지는 [Claude Code CHANGELOG](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)를 기반으로 주요 변경사항만 발췌하여 정리한 것입니다. 전체 내용은 원본을 참고하세요.
