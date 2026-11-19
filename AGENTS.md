# AGENTS.md — IAE_dev 제품 고유 실행 정책 (2026-11-19 KST)

## 0. 임무 잠금 및 정본 순위
- 현재 전용 제품: `hibi89/IAE_dev`. **임무**는 P0 설계를 기준으로 Windows 단일 UI+독립 엔진 어댑터의 개발 작업 시스템을 실제로 P1 코딩하고 P2 검증하는 것.
- `ㄱ`/`ㄱㄱ`은 이 IAE_dev 작업이 명시 고정된 채팅에서는 다음 실제 READY 수직 기능 구현. 해총 단독 채팅 `ㄱ`의 GitHub App→HMAC→Vercel→Actions→원장 업무 변경 금지.
- 사용자 최신 승인 > 해총 `OWNER_DEV_EXECUTION_CANONICAL_20261116.md` `0J / `GPT6_HIGH_STANDARD_WORK_UNIT_20261117.md` `0E 및 본 AGENTS > 실제 HEAD/소스·검증 근거 > HANDOFF/STATUS/큐 > 과거 이력.
- 먼저 repo/branch/정확 원격 HEAD → AGENTS → HANDOFF → STATUS → REQUIREMENTS/최종설계 → P1/P2 큐 및 실제 코드 확인. 원본 전문 엔진은 각 원본 repo·branch·AGENTS·정본·HEAD 우선.

## 1. 절대 제품 경계
- IAE_dev는 UI/adapter registry/evidence index/프로젝트 선택/지시·승인 경험만 소유한다. MLA=Controller/Owner/F18, FFAX=React/CSS·화면 충실도, REQ Auditor=정적 req/code 근거, AXZERO=경험 컴파일, EAI=비권한 advisor, 해총=관측.
- **AXZERO/EAI/AXNODE optional**: 없어도 MLA→FFAX→REQ/Actions 기본 흐름 유지. AXZERO의 EXECUTE_NO_AI 제안은 MLA 보호 권한을 대체하지 않는다. REQ 정적 근거는 실제 기능 검증/독립 감사가 아니다.
- 제품 원본 repository/main/타 브랜치/DB를 여기서 직접 수정·병합하지 않는다. 통합은 버전 pin·동의된 어댑터/API/CLI만. 역방향 의존성 도입 금지.

## 2. 구현·검증·보안
- P1 구현 후보 **IAE-SWU-001..022 (22)**, 요구사항 **IAE-REQ-01..28**, 작업 수용 기준/allowed_paths·의존성은 P1_SWU_TASK_QUEUE.json. 실제 BE/FE/DB/API/CLI caller→callee 정상/핵심 실패 경로, 국소 syntax/type/smoke, 민감 보안 즉시 검사는 필수.
- 현행 웹 GPT-6 Sol High는 12월 변경 실제 적용·모델 가용성·사용자 전환 결정 전까지 P0 및 P1 실제 코드·커밋 통합 담당. CPAA 위험·임계경로→한 번의 `ㄱ` 1~6 실제 READY SWU, 의존/동일 파일 충돌 안전 순서. 전체 P2 CI/브라우저는 일괄 후행, 기존 필수 CI 해제 금지.
- P2 **IAE-P2-01..09** 전부 P1 22/22 실제 후보/High 정확 SHA 게이트 전 LOCKED; 실 Windows11/EXE, 소스·CI·보안·통합·회귀·브라우저·복구·UX·자원 검증. P3 독립 기술·보안 및 UI/UX 감사, P4 High 인수, P5 사용자 GO.
- 자기가 작성한 코드를 자기가 검사해도 독립 감사로 승격 불가. 모델 생성 테스트 PASS=독립 F18 아님. `IMPLEMENTED_UNVERIFIED` ≠ `VERIFIED`. 분모/가중치 없으면 공식 % `UNASSESSED`.
- 실패 2+2: SWU당 실제 무진전 코드 시도 2회→격리·재설계, 다른 대안 2회→Sol Max 전문 배치. 고위험 임계경로는 0회부터 근거 갖춰 Codex(코드/보안/CI) 또는 Work(현장 브라우저) 지원 제안 가능. 확인 못한 모델은 MODEL_UNVERIFIED.
- **MLA Zero-VM/F18 유지**: VM, WSL2, Docker 등 설치를 요구하지 않는다. 미검증 생성 코드/테스트/임의 shell·exec 실행 금지; 제한 typed operator만, 원본/신뢰 경계 불충분 시 HOLD. 위험 입력에서도 fail closed.
- 승인 필요: 유료, 외부 민감/고객 원본 전송·변조, 권한/보안/OS 키·SCM/ACL/서비스 변경, 위험 DB·기존 기능 축소, remote 자동 쓰기, main merge, Production/도메인/환경변수, 상용 출시.
- 비밀키/.env/고객 자료/모델 파일/개인 로그/실 DB 공개 GitHub 업로드 금지. 백업·커밋 이력 보존, force push·임의 author 변경 금지.

## 3. 소스 작업 및 인계
- `dev/iae-dev-p1-20261119`에서만 실제 IAE-dev 앱 구현; `design/iae-dev-final-v1`은 최종설계 정본, `verify`는 P2, `feature/*`는 비충돌 분리 경로, `integration`은 승인이 확인된 실제 SHA만.
- 각 SWU 완료 기준: 실제 사용자 호출→기능→검증 가능 결과, 정확 source SHA + 실행한 syntax/type/smoke 결과. P1/P2/감사/GO 별도 원장 갱신. 단순 문서·mock·테스트 수 증가 완료 금지.
- 모든 커밋 전 branch/head 다시 확인하고 동일 ref 동시 쓰기 금지. 큰 변경이 끝나면 STATUS/HANDOFF 목표·완료·검증·차단·다음 READY·KST·SHA 갱신.
- 현 시점은 **P0 설계/분기 생성만**; 22개 P1 소스 작업 전부 계획, P2 9개 전부 LOCKED. 설계 문서·브랜치 생성으로 구현률 상승 금지.
