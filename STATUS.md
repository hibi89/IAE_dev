# STATUS — IAE_dev (2026-11-19 KST)

## 설계/저장소
- 저장소: `hibi89/IAE_dev` (PUBLIC); `main` 최초 안내 README. 설계/구현/통합/검증/기능 브랜치 목적은 `docs/BRANCH_STRATEGY.md`.
- P0 통합 최종설계 및 **28개 IAE REQ·22개 P1 SWU·9개 P2 게이트**를 중앙 정본에서 이식. 원본 엔진 목록/단계별 API·보안·작업지침도 문서화.
- **원격 정확 HEAD:** 본 문서는 최초 설계 baseline. 재개 때 `fetch_commit(repo, branch)`로 현재 HEAD 재확인. 문서 blob SHA와 Git commit SHA 다름.

## 구현·검증 분리
- **IAE_dev 앱 소스 P1:** `0/22 SWU` 실제 구현 후보, 28/28 요구사항 **미구현**. 설계·문서·branch 작업은 구현 SWU로 인정하지 않는다.
- **P2:** `0/9` 실제 검증 실행, **LOCKED**. P3 독립 기술·UI 감사 NOT_RUN, P4 High 수용 NOT_RUN, P5 OWNER GO false / RELEASE HOLD.
- 공식 가중 구현/검증률: `UNASSESSED`. 제품별 기존 구현률·검증률을 IAE_dev 새 22 SWU 분자에 합치지 않는다.
- IAE_dev Windows EXE·통합 사용자 대시보드 작동·MLA/FFAX/REQ 실제 E2E·AXZERO 학습/무AI 실행·Owner PC 검증: **NOT_RUN**.

## 현재 위험·구성
- MLA 11/19 진행, 보호 F18·Owner 권한과 CodeShield 미완 수용이 차단; FFAX 실레퍼런스 F95 미검증; REQ 감사는 정적 후보, P2 일부 범위한정 수용; AXZERO 자체 0/18 P1, 선택 연동으로 HOLD.
- 첫 실구현 목표: **하나의 프로젝트를 선택해 원격 설계/HEAD 확인→작업 계획 preview→MLA 상태/실 후보→REQ/Actions 실제 SHA 증거를 UI에 표시**하는 안전 수직 경로.
- 최초 후보 SWU: `IAE-SWU-001/002/005/006`. 실제 READY는 제품 소스 브랜치 생성·HEAD/AGENTS/승인/allowed_paths 검사 후 CPAA로 결정.

## 변경 안전
- 원본 제품/해총 운영·main·Production·권한·고객 자료·비밀·외부 비용·상용 배포 변경 없음.
- 2026-11-30 목표는 일정 희망. 실제 성공/속도·모델 절감 효과 UNMEASURED.
