# IAE_dev — 개인용 AI 개발 통합 워크스테이션

**IAE의 첫 번째 생태계 / Windows 로컬 앱 + 통합 대시보드 + 독립 엔진 어댑터.**
**2026-11-19 KST 상태: P0 설계 기준선만 / IAE_dev P1 0/22 SWU 코드 / P2 0/9 실행 / 공식 가중률 UNASSESSED / RELEASE HOLD.**

## 이 저장소에서 먼저 읽을 문서

- [AGENTS.md](AGENTS.md): 권한·현재 임무·SWU/P1/P2 실행 기준
- [STATUS.md](STATUS.md), [HANDOFF.md](HANDOFF.md): 현재 공식 상태, 다음 READY, 인계
- [설계 정본](docs/strategy/IAE_DEV_FINAL_BLUEPRINT_V1_20261119.md): 구조·기술·전체 기능·역할/안전 경계
- [28개 REQ + 22개 SWU + 9개 P2 수용 게이트](docs/strategy/IAE_DEV_IMPLEMENTATION_AND_ACCEPTANCE_V1_20261119.md)
- [기계 판독형 요구사항](REQUIREMENTS.md) · [P1 큐](P1_SWU_TASK_QUEUE.json) · [P2 큐](P2_VERIFICATION_TASK_QUEUE.json)
- [전문 엔진 목록](docs/ENGINE_CATALOG.md) · [연동 계약](docs/INTEGRATION_CONTRACTS.md) · [기술 스택](docs/TECH_STACK.md)
- [브랜치 구조](docs/BRANCH_STRATEGY.md) · [실제 구현 지침](docs/IMPLEMENTATION_RUNBOOK.md) · [보안·검증](docs/SECURITY_AND_ACCEPTANCE.md)

## 프로그램 구성

| 영역 | 프로그램/엔진 | 기본 경로 |
|---|---|---|
| 단일 Windows 사용자 화면 | IAE_dev React/TS 통합 UI, 향후 패키징 | 필수 |
| 개발 Controller/로컬 모델 | [MLA](https://github.com/hibi89/my_local_ai) · Ollama/Qwen3 · CodeShield/F18 | 필수 |
| 레퍼런스→FE | [FFAX](https://github.com/hibi89/frontend-foundry-ax) | 필수 |
| 디자인 자료·취향 | IAE Design Intelligence (로컬 신규) | 필수 |
| REQ↔실제 코드 증거 | [REQ Evidence Auditor A](https://github.com/hibi89/REQ-Evidence-Auditor-A-) | 필수 |
| 실제 CI·Git 원장 | GitHub / Actions / 로컬 검증기 | 필수 |
| 중앙 관측 | [해총](https://github.com/hibi89/hackathon-command-center-2026) | 읽기 전용 |
| 경험의 프로그램화 | [AXZERO](https://github.com/hibi89/Freelancer/tree/product/ax-zero-local) | 선택형, 미구현 |
| 추가 분석·전략 | [EAI](https://github.com/hibi89/EAI) | 선택형 |
| 능력·증거 포맷 | [AXNODE](https://github.com/hibi89/Freelancer/tree/product/axnode-sector-runtime) | 선택형 |

**핵심 흐름:** 프로젝트 선택/확정 SHA → MLA 작업·FFAX FE → REQ 정적 증거 + 실제 Actions/로컬 검증 → P2 → 독립 기술·UI 감사 → 사용자 GO. AXZERO/EAI/AXNODE OFF에서도 기본 경로가 동작해야 한다.

## 작업 브랜치

- `main`: 빈 repo 최초 README 기준선; 별도 GO 전 제품 통합/출시/병합 금지.
- `design/iae-dev-final-v1`: 이 P0 설계·요구사항·계약·큐의 정본.
- `dev/iae-dev-p1-20261119`: P1 실제 앱/BE/FE 코딩 작업.
- `integration/iae-dev-e2e-20261119`: 허용된 정확 SHA 통합 후보.
- `verify/iae-dev-p2-20261119`: 전체 검증·결함 수정, P1 SHA 게이트 전 LOCKED.
- `feature/iae-design-intelligence-20261119`: 디자인 지능화 비충돌 작업.
- `feature/iae-axzero-adapter-20261119`: AXZERO 어댑터 비충돌 작업; 원본 엔진은 별도 repo.

**현재 이 브랜치들의 존재가 소스 구현을 뜻하지 않는다.** 구현/검증/독립 감사/Windows 실기기 모두 실행해야만 증거에 반영한다.

## 운영 원칙

- `ㄱ`/`ㄱㄱ`은 **선택된 IAE_dev 개발 임무/프로젝트**만 진행. 해총 채팅 단독 `ㄱ`은 기존 GitHub App 자동화만.
- 사전 승인 없는 main·Production·도메인/환경변수·유료·외부 원본 송신·권한/보호서비스 변경/고객 DB 변조/상용화 불가.
- 공개 GitHub에 토큰, 개인 파일, 고객 원본, 모델 가중치, SQLite/로그/백업을 업로드하지 않는다.
- GitHub SHA·테스트 PASS·Windows 실기기 PASS·독립 감사·사용자 GO는 **다른 증거**다.

## 외부 AI 라우팅 (2026-11-20 정책)
**Qwen 로컬·검증된 AXZERO 우선 → Flash 일반 외부 지원 → Hydrogen 특별 난제만.** 사용자가 원한 3.5 Flash 역할을 보존하되 Google 공식 2026-10-08 deprecated 안내에 따라 `gemini-3.6-flash` API 후보를 **계정 확인 후** 사용한다. Hydrogen은 **로컬 rolling24h 20회 상한, 4회 긴급 예약**이며 provider 공식 한도가 아니다. 둘 다 **기본 OFF**이고 무료 계정/쿼터·별도 데이터 전송 승인이 필요하다.
- [전체 외부 AI 설계·한도·안전](docs/EXTERNAL_AI_ROUTING_V1_20261120.md)
- [기계 판독 예산 정책](data/EXTERNAL_AI_ROUTING_POLICY_V1.json)
