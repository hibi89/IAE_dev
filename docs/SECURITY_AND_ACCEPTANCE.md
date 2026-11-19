# SECURITY / P2 ACCEPTANCE — IAE_dev 보안·검증·출시 경계

- **원본과 민감정보:** customer/private 원본, 토큰, .env, 개인 logs/DB/백업, 모델 weights, 계정/접근키를 public GitHub에 올리지 않는다. 신뢰되지 않은 이미지·SKILL.md·AI 출력·Git 원격 콘텐츠는 모두 untrusted.
- **파일/코드:** canonical path·symlink/reparse/TOCTOU·Git SHA/CAS·허용 경로·diff·감지된 변경 소스 검증. 임의 shell/exec·생성 테스트/패키지 hooks·auto-install 금지. MLA Zero-VM/CodeShield/F18 보호 경계 유지.
- **로컬 웹:** loopback만 바인딩, Host/Origin/CSRF와 권한/요청자 분리, URL fetch SSRF·무단 외부 송신/요청 위조·이벤트 폭주 차단.
- **고위험 사용자 GO:** OS 서비스/SCM/HKLM/ACL/CNG·보안/권한, 원본·DB 변경, 외부 데이터 전송, 유료 계정/결제, 자동 원격 commit·main merge, Production/도메인/환경변수, 고객 실사용/상품화.
- **실제 증거:** GitHub Actions pass=해당 SHA의 해당 테스트만, 정적 REQ=근거 후보만, Owner Win11=실기기 실행 증거 필요, 외부 독립감사=제작자와 독립성 확인 필요. `NOT_RUN`을 PASS로 바꾸지 않는다.
- **P1/P2 분리:** P1에서는 문법·타입·국소 smoke+고위험 즉시안전 검사, P2에서 전체 CI/보안/통합/회귀/브라우저/Windows/성능/복구. 원본 repo 필수 CI 지속.
- **실패 2+2:** SWU 실제 무진전 2회→격리/재설계→다른 방법 2회→전문 지원 근거. 무관 READY 계속. 실환경·권한 차단은 코드 READY 위장 금지.
- **P2 게이트 9개:** `P2_VERIFICATION_TASK_QUEUE.json` + [상세 수용 계획](strategy/IAE_DEV_IMPLEMENTATION_AND_ACCEPTANCE_V1_20261119.md). 정확 소스 SHA·OS·CI run 및 PASS/FAIL/SKIP/NOT_RUN.
- **P3:** Codex/동등 외부 독립 기술·보안 + UI/UX 감사(실행했을 때만), **P4:** High 인수, **P5:** 사용자 GO. 상용 등록완료는 실제 URL·게시일 필수.

## 2026-11-20 외부 AI 안전 게이트
- 모든 provider API 기본 OFF, `max_spend_usd=0`. 무료 tier·account RPM/TPM/RPD, API 모델 실제 가용성, 공개/합성 비민감 데이터 분류·요청별 사용자 승인 없으면 BLOCK.
- 고객/비공개 원본·인증/토큰/.env·개인 데이터·비밀·미허가 이미지/프롬프트 외부 전송 금지. 자동 결제/계정 티어 변경/외부 모델 권한 승격 금지.
- Hydrogen 로컬 rolling24h 최대20, 긴급예약4, 동시1·작업1·재시도0. Flash 실패 429는 Hydrogen 자동 사용 허가 아님; 전송 불명은 UNKNOWN_CONSUMED.
- P2-05/06/09에 20/21번째 호출, 4 예약, 동시 예약, 중복·전원손실·401/403/429·모델 이동·실계정 free gate 및 비밀 전송 공격, mock≠live PASS 판정을 추가. 사용자 GO 없는 실 API NOT_RUN.
