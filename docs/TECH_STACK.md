# TECH STACK — IAE_dev 기술 구성과 선정 단계

| 계층 | 기본/재사용 기술 | 채택 상태 | 실제 검증·주의 |
|---|---|---|---|
| Windows 사용자 앱 | Win11 로컬 설치형 | 제품 형태 확정 | 아직 실행/패키징 NOT_RUN |
| UI | React + TypeScript + CSS | P0 우선 구현 경로 | FFAX 결과 재사용, a11y/IME/DPI 실제 P2 |
| 앱 셸 | Tauri 2 + Rust + WebView2 | **평가 후보** | Electron / 기존 Python Tk 등과 설치·메모리·sidecar·공급망 비교 |
| Python 엔진 | Python 3.11 stdlib + 기존 제품 CLI/API | 우선 경로 | OS 권한·자원/격리·호환 검증 |
| JS 도구 | Node.js/React/FFAX 번들 | 재사용 후보 | 패키징과 프로세스 lifecycle |
| 로컬 AI | Ollama + Qwen3:4B | MLA 기존 환경 | 모델 동시 상주 1개 기본, 개발/상용 성능 보장 없음 |
| 코딩 도구 | OpenCode, MLA Typed Operator | 기존 재사용 | 미검증 코드/테스트 직접 실행 금지, Zero-VM |
| 데이터 | SQLite WAL + 아티팩트 SHA-256 | 우선 경로 | IAE만 상태/증거 인덱스, 엔진 자체 DB는 각자 소유 |
| API·IPC | versioned JSON contract, 제한된 127.0.0.1/프로세스 IPC | P0 설계 후보 | Host/Origin/CSRF·프로세스 권한·신뢰 경계 검증 |
| Git SCM | Git, GitHub API, gh CLI, SHA pin/worktree | 원본 시스템 | 자동 remote write 별도 GO; force push 금지 |
| 코드 분석 | REQ Auditor Python AST, 각 제품 tests | 기존 재사용 | 정적 후보≠실제 PASS |
| CI/안전 | GitHub Actions, pytest, Ruff/mypy(해당 제품), TypeScript checks | 원본 시스템 | 정확 SHA/원본 RUN·SKIP·NOT_RUN 구분 |
| UI 테스트 | Playwright/Chromium | 제품별 사용 중 | 실제 owner Windows와 CI Windows Server를 구별 |
| 이미지 분석 | FFAX scene graph/capture 우선; OpenCV/Tesseract.js/pixelmatch | 선택/미확정 | 외부 자산 권리·정확도·RAM 검증 |
| Windows Python package | PyInstaller 필요 시 | 선택 후보 | unsigned build ≠ 검증/실행 승인 |
| 관측 | 해총 GitHub App/HMAC/Webhook/Vercel/Actions | 기존 운영 재사용 | IAE_dev는 조회, 기존 운영 구성 변경 없음 |

**필수 외부 유료 API 0**, **VM/Docker/WSL2 강제 0**. 실제 가격·시간·GPU/RAM·F95·무AI 재사용률은 `UNMEASURED`.
