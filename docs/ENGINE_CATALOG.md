# ENGINE CATALOG — IAE_dev에 들어가는 모든 프로그램

> 2026-11-19 관측 원격 HEAD 스냅샷. **매 작업 직전 다시 최신 ref와 제품 고유 AGENTS/HANDOFF/STATUS를 확인**한다. SHA는 의존 버전 정본 핀이 아니라 관측 기록이며 새 버전 호환성은 별도 검증한다. JSON 표: [ENGINE_REGISTRY.json](../data/ENGINE_REGISTRY.json).

## 0. 주 시스템
| 구성 | Repo/branch | 역할 | 필수/선택 | 미지원 대안 |
|---|---|---|---|---|
| IAE_dev 사용자 화면/호스트 | `hibi89/IAE_dev@dev/iae-dev-p1-20261119` | 프로젝트·명령·UI·프로세스·아티팩트·증거 원장 | 필수 신규개발 | 읽기전용 대시보드부터 |
| MLA/My Local AI | `hibi89/my_local_ai@dev/instant-implementation-v1` | Controller·Qwen/OpenCode·안전 실행·F18·Owner·Git | 필수 | 동의 없는 실행 HOLD |
| FFAX V3 | `hibi89/frontend-foundry-ax@feature/ffax-reference-fidelity-20261118` | reference scene→React/CSS·UI 실제 렌더·비교 | 핵심 FE | FE 작업만 HOLD, 독립 BE READY 계속 |
| REQ Evidence Auditor A | `hibi89/REQ-Evidence-Auditor-A-@integration/reqea-p1-20261118` | REQ와 코드 정적 증거·call graph·보고 | 필수 P2 근거 | 정적 결과 추정 금지, 게이트 HOLD |
| GitHub/Actions/gh CLI | 제품별 repo/ref | 원본 source SHA·실행된 CI·빌드·브랜치 기록 | 필수 원격 근거 | 오프라인 읽기/소스 cached 단, fresh PASS 아님 |
| 해총 | `hibi89/hackathon-command-center-2026@kmong-productization` | 중앙 상태/장애/상용 원장 관측 | 읽기 전용 | 중앙 장애 시 제품 로컬 작업 분리 |
| CodeShield+F18 | MLA의 보안 하위 경계 | 불신 코드/Owner/독립 검증 | 필수 실행권한 | 차단 시 HOLD, 우회 금지 |
| IAE Design Intelligence | `hibi89/IAE_dev@feature/iae-design-intelligence-20261119` | 로컬 레퍼런스·권리·검색/선택/취향 | IAE-dev 기능 필수 | 초기에는 허가된 파일·메타데이터만 |
| 독립 검증·승인 | 제품별 CI + 독립 리뷰어 + Owner GO | P2/P3/P4/P5 구별 | 출시 필수 | 독립 검증 불가면 미승인 |

## 1. 선택형 도구
| 구성 | 원본 | 역할 | 주의 |
|---|---|---|---|
| AXZERO | `hibi89/Freelancer@product/ax-zero-local` | Trace→pattern→typed IR→검증 후보→NO_AI 추천/rollback | AXZERO 설계만, P1 0/18. MLA Owner/F18을 우회할 수 없음 |
| EAI V3.2 | `hibi89/EAI@feature/eai-v32-owner-rebuild-20261119` | 진단/추가 CPU 분석·전략 제안 | advisor 전용; 승인·실행권 없음 |
| AXNODE | `hibi89/Freelancer@product/axnode-sector-runtime` | 포터블 능력/근거 serialize/export | 저장/배포=실행·검증 PASS 아님 |
| 외부 LLM/Hydrogen/Codex/Work | 계정·가용성·승인 별도 | 고급 판단/독립 검수/현장 GUI | 무료·로컬 우선, 모델/인증/권한·유료/외부 전송 별도 GO |

## 2. 중복 개발 금지
- **MLA만** 작업 큐·Owner 승인·F18의 권한 있는 Controller. IAE_dev에서 새로운 독립 실행 Controller를 재제작하지 말 것.
- **REQ Auditor만** 정적 코드그래프/REQ 근거. 이 결과가 실제 통합 테스트 PASS가 되지는 않는다.
- **FFAX만** 레퍼런스 scene graph·렌더·React 생성, Design Intelligence는 자료 관리/FFAX 입력 패키지만.
- **AXZERO만** 경험 컴파일·무AI 모듈 후보. IAE_dev는 AXZERO bridge만, 사용자 경험상 MLA 작업 화면에 내부화하되 소스는 독립 보존.
- **해총** GitHub App→HMAC→Vercel→Actions 운영과 장애 알람은 기존 것 재사용. IAE_dev는 상태 조회·대조만.
