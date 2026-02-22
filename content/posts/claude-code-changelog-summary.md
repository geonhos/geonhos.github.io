---
title: "Claude Code 업데이트 핵심 정리 (v1.0 ~ v2.1.50)"
date: 2026-02-22
draft: false
tags: ["Claude Code", "Anthropic", "AI", "CLI", "Changelog"]
summary: "Claude Code의 주요 업데이트를 버전별로 핵심만 추려 정리합니다. 모델 업그레이드, 신규 기능, 플랫폼 지원 등 메이저 변경사항을 한눈에 볼 수 있습니다."
---

> 원본: [anthropics/claude-code CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
>
> 마지막 업데이트: 2026-02-22 (v2.1.50 기준)

---

## 모델 업그레이드 이력

| 버전 | 모델 변경 |
|------|----------|
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
