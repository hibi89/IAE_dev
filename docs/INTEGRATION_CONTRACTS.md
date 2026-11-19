# INTEGRATION CONTRACTS — IAE_dev와 독립 엔진 사이의 경계

> P0 입력/출력 **예상 계약**. 각 제품의 최신 실제 CLI/API를 조회해 adapter 구현 시 협의·버전 고정한다. 현재 이 인터페이스 구현/실 E2E NOT_RUN.

## IntegrationRequestV1
`request_id, project_id, repo_full_name, branch, expected_head_sha, design_sha, policy_sha, swu_ids, req_ids, allowed_paths, owner_scope, requested_effects, risk_tier, timeout_ms, cpu_ram_budget, reference_asset_digests`

## IntegrationResultV1
`request_id, engine, engine_version, source_sha, artifact_sha, evidence_sha, evidence_uris, result_kind, decision, actual_model_calls, elapsed_ms, blockers, requires_owner_approval`

`decision`과 `status`는 **비권한성 결과 데이터**다. `READY/RUNNING/IMPLEMENTED_UNVERIFIED/PARTIAL_PASS/SCOPED_PASS/VERIFIED/HOLD/BLOCKED_TRUST/NOT_RUN`은 **증거의 담당/출처/샤**와 함께 별도 원장에 저장. 누구도 boolean 하나로 P1/P2/독립감사/Owner GO를 합치지 않는다.

## 필수 어댑터
- **MLA:** 선택 프로젝트의 작업·scope·F18·Owner·현재 SHA를 검증한 뒤 명시적으로 허가된 상태 조회/작업 후보만. MLA Source/TrustedReceipt가 최종.
- **FFAX:** `SelectedReferencePackageV1`(원본/사용권/viewport/DPR/asset SHA/fixed vs variable) → 실제 scene/React/CSS/Chromium screenshot/사용자 review evidence. 이미지 파일 업로드는 로컬/권리 확인/승인 하에서만.
- **REQ-A:** 정확 REQ 디자인/코드 SHA 기반 정적 proof candidates/graph. `PASS_STATIC`은 전체 P2 PASS 아님.
- **GitHub:** 정확 HEAD·commit·workflow run/job SHA 읽고 네트워크/권한/404/429/오프라인을 구분. remote write는 사용자 별도 scope 승인.
- **해총:** 중앙 상태·장애·원장 읽기 전용. GitHub App·Webhook·Vercel 배포·Actions 구성을 IAE_dev가 변경하지 않는다.

## 선택 어댑터
- **AXZERO:** trace→candidate_compilation/artifact SHA/validator SHA/policy→NO_AI 제안; MLA F18/Owner 승인 이후에만 실행. 계약 불일치/미구현은 `NOT_AVAILABLE/OFF`로 기록하고 기본 개발 작업을 계속.
- **EAI:** 선택된 CPU/전략 advisor 결과만; 최종 명령/권한/검증 판정 없음.
- **AXNODE:** 검증 능력 serialize/export 선택; runtime 신뢰·호환 시험은 별도.

## 모든 어댑터 실패 처리
1. `capabilities/version` handshake, refs·서명/해시·owner scope·allowed effects/paths 검증
2. 제한된 호출 시간/자원/재시도, correlation request_id/attempt_id, idempotent receipt
3. timeout/중단/정책 불일치/권한 없음/stale SHA/malicious input/OOD이면 typed HOLD, 관측 근거 보존
4. 한 모듈 장애는 다른 독립 READY 진행 허용. 단, REQ/Actions 미연결 때 실제 P2 PASS로 조작 금지.

## 2026-11-20 ProviderRequestV1 / ProviderResultV1 계약
**ProviderRequestV1:** `request_id, project_id, source_sha, provider_role, requested_model_id, data_class, rights_clearance, sanitized_payload_sha, owner_approval_id, free_tier_snapshot, quota_snapshot, max_cost_usd, deadline_ms, attempt_id`.
**ProviderResultV1:** `request_id, effective_response_model_id, receipt_sha, status, reason_code, usage_tokens, observed_cost_usd, latency_ms, consumed_quota_state, untrusted_candidate_ref`.
- External provider registry는 OFF/free-account-unverified/egress forbidden일 때 호출 거부, Flash의 deprecated alias를 3.6 API 실모델 검증 뒤 핀, Hydrogen rolling24h 20/긴급4/작업1·동시1·재시도0 원자 예약.
- 429/timeout/오류에 Hydrogen 자동 escalation 금지; 불명확한 전송은 UNKNOWN_CONSUMED. 모델 답변은 UNTRUSTED_PROPOSAL이며 MLA F18/Owner를 우회하지 않음.
- [정본](EXTERNAL_AI_ROUTING_V1_20261120.md) · [기계 정책](../data/EXTERNAL_AI_ROUTING_POLICY_V1.json)
