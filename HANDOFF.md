# HANDOFF — IAE_dev P0 설계/브랜치 기준선 (2026-11-19 KST)

1. **목적/임무:** Windows 11 GTX1050Ti/16GB 개인용 단일 IAE_dev 작업대. 기존 MLA·FFAX·REQ/Actions+해총 연결, Design Intelligence 신규; AXZERO/EAI/AXNODE 선택형. 실제 개발 엔진은 중복 구현하지 않는다.
2. **설계 정본:** `design/iae-dev-final-v1:docs/strategy/IAE_DEV_FINAL_BLUEPRINT_V1_20261119.md` 및 `...IMPLEMENTATION_AND_ACCEPTANCE_V1_20261119.md`. 중앙 원본은 `hibi89/hackathon-command-center-2026@kmong-productization` HEAD `313e1b6cdb5b0dfa2a11b323d347d84db08a1467`.
3. **실제 상태:** 신규 IAE_dev 앱 소스 미작성, P1 `0/22` 후보·28 REQ 구현 0개, P2 `0/9` NOT_RUN/LOCKED, 공식 가중률 UNASSESSED, P3/P4/P5 NOT_RUN/HOLD. 새 브랜치·문서 = 코드 구현 아님.
4. **원본/엔진:** `docs/ENGINE_CATALOG.md`·`data/ENGINE_REGISTRY.json`의 각 repo/branch/관측 SHA 확인 후 작업마다 최신 HEAD 재조회; 타 제품의 P2 통과를 추정하지 말 것.
5. **선행/READY:** `P1_SWU_TASK_QUEUE.json` 전체 `PLANNED_NOT_READY`. 개발 브랜치 원격 HEAD/허용 경로·정본 일치·승인 재평가 후 `IAE-SWU-001`(프로젝트 선택), 다음 `002`(정확 SHA·설계 로드), `005`(증거 원장), `006`(adapter registry); 의존성 순서와 실제 코드 충돌 확인.
6. **병목:** MLA 보호 Owner/F18/Zero-VM, FFAX 실사용 레퍼런스, REQ Owner Win11/P2, AXZERO 미구현, IAE-dev EXE/실기기 NOT_RUN. 외부·관리자 권한 없으면 해당 SWU HOLD, 다른 안전 READY 계속.
7. **실행 기본:** Python3.11/SQLite-WAL/React TS, CLI/API 통합, 로컬 모델 1개, 읽기전용 우선. Tauri2/WebView2 + Python sidecar는 우선 **평가 후보**, Electron/Tk 대조. 실 패키징/설치 NOT_RUN.
8. **안전/원본:** 사용자 GO 없는 remote write·main·Production·보호 권한·고객 원본·결제/상용화 불가. 공개 GitHub secrets/DB/로그 업로드 금지. 기존 GitHub App 해총 단독 `ㄱ` 임무 불변.
9. **검증:** 본 설계 출처·파일 자체 GitHub 원격 기록만; 실제 Windows/브라우저/코드/외부 모델 테스트와 독립 감사 NOT_RUN.
10. **다음 실행:** IAE_dev 전용 새 작업 채팅을 잠그고 `ㄱ` → 최신 HEAD/정본/큐 확인 → 1~6 READY 실제 수직 기능 구현·국소 검사·GitHub 커밋 → STATUS/HANDOFF 갱신. P2/독립 감사/GO는 별도.

## 2026-11-20 — Flash/Hydrogen P0 설계 추가 인계
- 경로: 검증된 AXZERO/MLA Qwen 로컬 우선 → Flash 일반 외부 자문 → Hydrogen 특수 난제만. **Google 공식 3.5 Flash deprecated→3.6 Flash API**, 실제 무료 tier/계정 한도/유효 모델 ACCOUNT_UNVERIFIED.
- Hydrogen 사용자 자체 운영 예산: rolling24h 최대20, 긴급용 4 예약, 작업당 1회, 동시1회, 자동재시도 0. Flash 429로 자동 Hydrogen 호출 금지. 외부 전송·API·과금/키·계정 설정 NOT_RUN/OFF.
- [모델 상세설계](docs/EXTERNAL_AI_ROUTING_V1_20261120.md)와 [계약 JSON](data/EXTERNAL_AI_ROUTING_POLICY_V1.json), IAE-SWU-006/007/018/019/020 및 P2-05/06/09에 귀속. IAE-dev 실제 코드 P1 0/22, P2 0/9 LOCKED. 본 반영은 docs only, 해총 고유 임무·원본 제품 정본 변경 없음.
