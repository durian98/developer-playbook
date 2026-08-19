# Engineering Playbook

프로젝트를 하다 남는 건 코드만이 아니다. 선택의 이유, 한 번 놓친 조건, 다음에는 먼저 확인할 질문도 남는다.

이곳은 그런 메모를 모아 두는 개인 플레이북이다. 기술 개념을 다시 설명하기보다, 실제 작업에서 검증한 판단과 실패 경험을 다음 프로젝트에 가져갈 수 있는 형태로 정리한다.

**처음이라면 [Question First](mindset/question-first.md)부터 읽으면 된다.**

## 이곳에 있는 것

| 문서 | 언제 보면 좋은가 |
| --- | --- |
| [Mindset](mindset/question-first.md) | 무엇부터 확인할지 막막할 때 |
| [Prompts](prompts/) | 작업 단계에 맞춰 AI에게 질문을 던지고 싶을 때 |
| [Checklists](checklists/) | 구현 전후에 놓친 조건이 없는지 빠르게 볼 때 |
| [Failure Patterns](failure-patterns/) | 실패 조건을 재현하고 검증 방법을 찾을 때 |
| [Cases](cases/) | 실제 상황에서 어떤 선택을 했는지 살펴볼 때 |
| [Templates](templates/) | 프로젝트 경험을 이 저장소에 옮길 때 |

## 읽는 순서

작업을 시작할 때 모든 문서를 읽을 필요는 없다.

```text
무엇을 만들어야 하지?
  └─ Question First

어떤 구조로 시작할까?
  └─ Architecture / Design prompt

구현은 됐는데, 어디가 불안하지?
  └─ Senior Review / Failure Analysis

다음에도 이 판단을 쓸 수 있을까?
  └─ Case 또는 Checklist로 정리
```

프롬프트는 답을 대신 정하는 도구가 아니다. 놓치고 있던 가정과 확인할 위험을 드러내기 위해 쓴다.

## 남길 만한 기록

- 요구사항 속에서 실제로 중요했던 제약
- 비교한 선택지와 선택한 이유
- 동시 요청, 재시도, 부분 실패처럼 뒤늦게 드러난 문제
- 테스트, 로그, 측정으로 확인한 결과
- 다음 작업에서 먼저 물어볼 질문

검색으로 찾을 수 있는 기술 정의, 직접 겪지 않은 패턴 요약, 근거 없는 규칙은 남기지 않는다. 사건 자체보다 그 경험에서 다시 쓸 수 있는 판단을 남긴다.

## 현재 사례

- [엣지 모델 선택은 정확도와 실제 실행 경로 비용을 함께 고정](cases/edge-model-selection-and-runtime-budget.md)
- [테스트 실행 환경과 이미지 빌드 책임 분리](cases/ci-test-and-image-build-boundary.md)
- [이벤트 수신 범위와 빌드 대상 분리](cases/webhook-trigger-and-build-scope.md)
- [시연 UI는 실제 이벤트 파이프라인을 호출한다](cases/demo-actions-through-real-pipelines.md)
- [웹훅의 전송 형식과 목적지를 분리 검증한다](cases/webhook-contract-and-routing.md)
- [배포 준비 상태와 운영 의존성 상태 분리](cases/deployment-readiness-and-operational-health.md)
- [실시간 알림과 영속 이벤트의 생명주기 분리](cases/notification-lifecycle-and-event-history.md)
- [장치 이벤트 판정 교체는 Shadow 검증 뒤 전환](cases/device-event-cutover-with-shadow-mode.md)
- [공개 진입점과 서비스 노출 경계를 함께 설계](cases/public-ingress-and-service-exposure.md)
- [혼합 센서 조준은 판정과 정지 기준을 분리](cases/visual-servoing-sensor-and-control-boundary.md)
- [장기 실행 하위 프로세스는 소유권과 종료 경계를 둔다](cases/subprocess-lifecycle-and-process-group-cleanup.md)

## 프로젝트 경험을 옮길 때

프로젝트의 `context/playbook-export.md`에 검증된 후보 한 건을 적고, 그 후보를 지정해 반영을 요청한다. 프로젝트의 상세 기록과 원문 로그는 원래 프로젝트에 남긴다.

이 저장소에는 중복과 민감정보를 확인한 뒤, 다른 작업에도 도움이 될 내용만 옮긴다. 반영 기준과 문서 작성 규칙은 [AGENTS.md](AGENTS.md)에 있다.
