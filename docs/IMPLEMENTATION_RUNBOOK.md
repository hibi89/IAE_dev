# IMPLEMENTATION RUNBOOK — IAE_dev 전용 새 채팅/코딩 재개

1. **고정 임무:** `hibi89/IAE_dev` 제품. 현재 HEAD가 설계/코드인 각 branch 확인. `main` 직접 작업·병합 금지. 해총 단독 `ㄱ`의 GitHub App 임무 불변.
2. **읽기 순서:** 최신 GitHub 원격 HEAD → AGENTS → HANDOFF → STATUS → REQUIREMENTS / 최종설계 → P1/P2 JSON 큐 → 실제 코드. 원본 MLA/FFAX/REQ/AXZERO 최신 제품 계약/승인/안전도 따로 확인.
3. **CPAA 선정:** 의존 DAG, 후속 차단 수, S/C/I/D/U, allowed_paths, 위험·권한·파일 충돌/비용을 따져 독립 READY 1~6개. 계획 `PLANNED_NOT_READY`는 실제 README/브랜치만으로 READY가 아니다.
4. **P1 실행:** 실제 사용자 호출에서 BE/FE/DB/API/CLI/caller→callee, 정상·핵심 실패 경로, 필수 국소 syntax/type/smoke + 고위험 보안 즉시 검사 → GitHub source SHA 확인. docs/Mock/화면 단독 진척 인정 안 함.
5. **브랜치:** `dev/iae-dev-p1-20261119`에 기능, `feature/*`는 동일 시작 SHA·비충돌 파일만, `integration`은 검토된 ref만; 검증 SHA 통합·정본/실행 이력 보존. 동일 ref 동시 쓰기, force push 금지.
6. **P2 잠금:** 22/22 P1 후보 + 정확 SHA High P1 게이트 후 `verify/iae-dev-p2-20261119`에서 9개 수용. Windows/실기기/CI/브라우저/보안/복구·결함 수정, 독립감사는 별도. P3/P4/P5도 별개.
7. **처리/보고:** SWU/REQ 완료 실제 수/분모, 구현률과 검증률 각각, SHA, 실제 PASS/FAIL/SKIP/NOT_RUN, 막힘·승인·다음 READY, KST, 소스·정본 SHA. 기계 큐·STATUS·HANDOFF를 함께 갱신.
8. **최소 첫 수직 기능:** 프로젝트 1개 선택→HEAD/설계 확인→scope 명령 preview→MLA 실제 작업 상태/후보→REQ/Actions 정확 SHA 근거 조회→UI에 차단/검증을 구분하여 표시. 선택형 AXZERO/EAI OFF 상태에서도 작동.
9. **비용/보호:** 무료 로컬/사용자 PC 개입 최소화, 비밀·고객 자료 외부 전송/관리자 권한·실행 코드·Production은 별도 GO. 실행 신뢰 경계 없으면 HOLD.

## 2026-11-20 Provider Router 실제 구현 선행
- 제품 분모 변경 없이 기존 IAE-SWU-006/007/018/019/020의 allowed_paths·수용조건에 provider 연결·MLA F18·egress policy·quota ledger·UI를 적용. P2-05/06/09 실제 회귀 추가.
- 분리 기능 브랜치 `feature/iae-provider-router-20261120`. 주 변경 경로 `adapters/external_ai/**`, `service/approval/**`, `service/storage/**`, `service/metrics/**`, `app/ui/providers/**`, `tests/security/**`. 동일 공통 파일 충돌 시 dev에서 단일 통합자가 해결.
- 데이터와 승인·실무료 계정/실 API 모델 ID 미확정 상태에서는 mock/synthetic만, 라이브 호출 OFF. Flash 429→Hydrogen 자동 승격 금지. 본 작업은 docs-only; 구현 진척 0.
