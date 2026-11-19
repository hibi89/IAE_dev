# IAE_dev — 개인용 AI 소프트웨어 개발 통합 작업대

> **상태 (2026-11-19 KST):** P0 설계 기준선 준비 중. 통합 EXE/실제 P1·P2 기능 구현 및 검증 NOT_RUN, RELEASE HOLD.

IAE 전체 비전의 첫 번째 생태계인 **IAE_dev**는 단일 Windows 앱/대시보드에서 MLA·FFAX·REQ Evidence Auditor·GitHub Actions와 선택형 AXZERO·EAI·AXNODE, 디자인 레퍼런스 라이브러리를 통합하는 개발 워크스테이션이다. 원본 엔진은 별도 저장소로 유지한다.

## 먼저 확인할 설계 정본

- [해총 IAE_dev P0 통합 최종설계](https://github.com/hibi89/hackathon-command-center-2026/blob/kmong-productization/docs/strategy/IAE_DEV_FINAL_BLUEPRINT_V1_20261119.md)
- [해총 28 REQ · 22 P1 SWU · 9 P2 수용계획](https://github.com/hibi89/hackathon-command-center-2026/blob/kmong-productization/docs/strategy/IAE_DEV_IMPLEMENTATION_AND_ACCEPTANCE_V1_20261119.md)

**정본·작업 브랜치 안내**는 `design/iae-dev-final-v1`에서 관리한다. `main`은 소유자 별도 승인 전 통합·출시 대상이 아니다. 해총 단독 `ㄱ`의 GitHub App 자동화 임무는 불변이며 IAE_dev 작업은 해당 제품 채팅에서만 실행한다.

민감 고객 자료·토큰·개인 파일·로컬 DB·원본·모델 가중치를 공개 GitHub에 올리지 않는다. 유료·외부 전송·권한 변경·main 병합·Production·상용 출시 별도 GO.
