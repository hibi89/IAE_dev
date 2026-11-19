# REQUIREMENTS — IAE_dev 신규 앱 28개 REQ

> 원본: [IAE_dev 구현·검증 정본](docs/strategy/IAE_DEV_IMPLEMENTATION_AND_ACCEPTANCE_V1_20261119.md). 제품 MLA/FFAX/AXZERO/REQ 자체 REQ는 **합치지 않는다**. 현재 REQ 28개 모두 IMPLEMENTED_UNVERIFIED가 아니라 NOT_IMPLEMENTED.

| ID | 영역 | 기능·수용조건 |
|---|---|---|
| IAE-REQ-01 | 프로젝트 | 사용자 선택 **단일** repo/project/branch; 선택 전 쓰기/`ㄱ` 시작 불가, 최근 프로젝트 변경 시 pending 승인 철회 |
| IAE-REQ-02 | 신뢰 핀 | repo/branch/current HEAD, 설계·정책 SHA 조회·고정; drift/stale/not found 시 HOLD |
| IAE-REQ-03 | 설계 | 최종설계·REQ·SWU·수용조건의 원본/버전/권한·읽기 권한 구분; 오염된 문서가 실행 권한이 되지 않음 |
| IAE-REQ-04 | 명령 | `ㄱ`/`ㄱㄱ`·자연어를 **선택 프로젝트만** scoped WorkIntent로 변환; 해총 채팅 명령 의미 불변 |
| IAE-REQ-05 | 승인 | 작업 범위/허용 파일/위험·효과·예산 preview, 별도 owner GO 없는 외부송신/권한/원본/remote write 차단 |
| IAE-REQ-06 | SWU DAG | depends_on/allowed_paths/S-C-I-D-U/차단·READY 계산; 순환/결손/경로 충돌 오류 검출 |
| IAE-REQ-07 | 재개 | CPAA 임계경로·1~6 안전 READY 웨이브, 2+2 실패 격리·재설계·체크포인트; 중복 실행 금지 |
| IAE-REQ-08 | 증거 원장 | 정확 source/plan/policy SHA, run/attempt, 분리된 P1/P2/독립감사/GO 상태, 증거 원문 링크·digest·부재 표시 |
| IAE-REQ-09 | MLA | 실제 MLA Controller 호환 핸드셰이크/읽기 상태; 보호 Owner·F18/Zero-VM 경계 우회 불가 |
| IAE-REQ-10 | 엔진 등록 | 버전·capability·CLI/API·프로세스/타임아웃·자원·OFF 스위치; 미설치·stale·invalid 응답은 타입화 HOLD |
| IAE-REQ-11 | 개발 후보 | 허용 실행에서 실제 BE/DB/API/CLI 소스 후보·diff·파일 경로·검사 증거를 수집; Git 원본 자동 덮어쓰기 금지 |
| IAE-REQ-12 | FFAX | 승인된 레퍼런스 패키지를 FFAX에 전달·React/CSS·viewport/DPR·캡처/수정 결과 받고 실제 FE 근거 추적 |
| IAE-REQ-13 | 디자인 수집 | 이미지/URL/영상·출처/권리/프로젝트/해시/로컬 경로·동의; 권리 미확인·네트워크 미허가 수집 차단 |
| IAE-REQ-14 | 디자인 선택 | 기본 16개 경량 참조 탐색·프로젝트별 선택/선호·정밀 소수 후보; 실제 생성/렌더는 FFAX 책임 |
| IAE-REQ-15 | REQ 감사 | A 통합 제품에서 실제 req↔code 정적 증거 수신, 정적 후보를 `VERIFIED`로 격상하지 않음 |
| IAE-REQ-16 | Actions | GitHub Actions workflow/commit SHA/run/jobs 실제 상태 읽기; 성공·실행안됨·다른 SHA/실기기 구분 |
| IAE-REQ-17 | 수용 단계 | P1 코드 후보와 P2 실제 PASS, 독립감사, Owner GO, 게시 URL·일자 분리; 분모/가중치 없는 완료율 `UNASSESSED` |
| IAE-REQ-18 | 독립검수 | 제작 참여 검수자의 셀프 PASS 독립감사 불인정; 정확 SHA·별도 리뷰어·범위·문제와 최종 인수 기록 |
| IAE-REQ-19 | diff·원본 | 코드 후보 diff/허용 경로/symlink/reparse/TOCTOU, 동일 ref 충돌·SHA 불일치 시 적용 중단 |
| IAE-REQ-20 | AXZERO | 검증된 trace·계약·artifact/evidence를 버전 핀한 선택형 port; 미구현/OFF에서 기본 경로 정상, MLA 승인 없는 `NO_AI` 실행 불가 |
| IAE-REQ-21 | EAI | 비권한 advisor 선택형; 미설치/OFF/오류에서 기본 MLA 결과 불변, 조언이 실행 GO가 되지 않음 |
| IAE-REQ-22 | 해총 관측 | 중앙 상태·장애·SHA를 읽기/정합성 비교; 해총 GitHub App 운영 권한·웹훅·Production 변경 없음 |
| IAE-REQ-23 | UI/UX | 프로젝트·명령·P1·P2·디자인·검사·감사·로그·사용량·차단 페이지; 한국어 IME·키보드/a11y·DPI |
| IAE-REQ-24 | Windows 앱 | React UI를 Tauri/Electron/네이티브 실측 비교 뒤 Win11 앱/sidecar 패키징; 설치·시작/종료·업데이트·제거/복구 검증 |
| IAE-REQ-25 | DB/복구 | IAE 자체 SQLite WAL 안전 인덱스, idempotency·중단/재시작·backups; 외부 엔진 DB 직접 변경 금지 |
| IAE-REQ-26 | 자원/KPI | CPU/RAM/VRAM·latency·actual model calls/토큰/비용·오류, 간접·가상 수치 제외; 저사양 동시 실행 한도 |
| IAE-REQ-27 | 보안/권한 | 기본 오프라인·외부 전송/설치/임의 생성코드 실행·main/Production/HKLM/SCM/ACL/CNG·결제는 별도 GO; fail-closed |
| IAE-REQ-28 | 호환·권리 | 기존 엔진 원본 보존·핀된 versioned adapters·라이선스/asset 권리; AXNODE 등 미래 모듈은 optional |
