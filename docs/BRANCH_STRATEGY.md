# BRANCH STRATEGY — IAE_dev 브랜치·담당·합류 경계

> 2026-11-19 최초 기준선. **모든 신규 브랜치는 처음에는 동일한 P0 문서 SHA를 가리킬 수 있으며 기능 구현 완료를 뜻하지 않는다.** 각 기능 담당은 작업 개시 전 최신 HEAD·충돌 파일·실제 READY 재확인.

| branch | 역할 | 허용 작업/책임 | 금지/게이트 |
|---|---|---|---|
| `main` | 초기 빈 레포 README 기반·향후 RELEASE | 초기 안내 외 자동 반영 금지 | 사용자 별도 GO 전 개발/검증 PR 병합·Production 금지 |
| `design/iae-dev-final-v1` | **IAE_dev P0 최종설계 정본** | AGENTS, REQUIREMENTS, docs, P1/P2 계획·계약·분모·안전 | 소스 구현/실환경 PASS 위장 금지 |
| `dev/iae-dev-p1-20261119` | 실제 P1 백엔드·프론트엔드 개발 | SWU-001..022 + 최소 검사 + 구현후보 기록 | 브랜치 보호/GO 우회, 미검증 런타임 실행 금지 |
| `feature/iae-design-intelligence-20261119` | Design Intelligence 격리 개발 | `design_library/**` `app/ui/library/**` `adapters/ffax/**`의 승인된 비충돌 범위 | 공통 API/DB 임의 변경·동일 파일 동시 수정 불가 |
| `feature/iae-axzero-adapter-20261119` | AXZERO 어댑터 격리 | `adapters/axzero/**` 및 해당 contract tests | 원본 AXZERO/MLA F18 권한 변경 불가; AXZERO 미구현 시 안전 OFF 경로만 |
| `integration/iae-dev-e2e-20261119` | 충돌 해결된 동일 SHA 통합·한 프로젝트 E2E | 소유자·통합자가 실제 받은 검증후보만 병합/검증 | 단순 branch 생성=통합 PASS 아님 |
| `verify/iae-dev-p2-20261119` | P2 전체 CI/보안/Windows/브라우저/복구 | P1 22/22 후보 및 High exact-SHA 게이트 이후 검증·결함 수정 | 게이트 전 P2 LOCKED, 독립 감사와 구분 |

**브랜치 흐름:** `design` 기준선 → `dev` 개발, 비충돌 `feature/*` → 정확 SHA/계약 확인 후 `integration` → 안전 인수된 SHA에서 `verify` P2 → P3 독립 감사 → P4 High 인수 → 별도 사용자 GO 시에만 `main`.

**다중 작업자 병렬**은 작업별 책임자·동일 출발 SHA·비충돌 allowed_paths·실제 총시간 이득/가용성이 검증될 경우에만 사용. 모델 한 명을 여러 병렬 작업자라고 주장하지 않는다. Force push/권한·브랜치 보호 임의 변경 금지.
