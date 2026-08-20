# Developer Playbook

프로젝트를 하면서 직접 겪은 문제와 그때 내린 판단을 정리해 두는 곳이다.

기술 개념을 다시 설명하는 글보다는, 실제로 어떤 문제가 있었고 무엇을 확인한 뒤 어떻게 결정했는지를 남긴다. 다음 프로젝트에서 비슷한 상황을 만났을 때 같은 실수를 반복하지 않고, 더 나은 질문부터 시작하기 위한 기록이다.

처음 볼 때는 [Question First](mindset/question-first.md)부터 읽으면 된다.

## 문서 찾기

| 문서 | 언제 보면 좋은가 |
| --- | --- |
| [Mindset](mindset/question-first.md) | 작업을 시작하기 전에 무엇부터 확인할지 정리할 때 |
| [Prompts](prompts/) | 설계, 구현, 검증, 회고 단계에서 AI와 함께 점검할 때 |
| [Checklists](checklists/) | 구현 전후에 빠뜨린 조건이 없는지 확인할 때 |
| [Failure Patterns](failure-patterns/) | 비슷한 장애를 재현하고 원인을 좁힐 때 |
| [Cases](cases/) | 실제 경험에서 어떤 판단을 내렸는지 찾아볼 때 |
| [Templates](templates/) | 새 프로젝트의 경험을 같은 형식으로 정리할 때 |

## 사용하는 순서

매번 모든 문서를 읽을 필요는 없다. 지금 하는 작업과 가까운 문서만 골라 본다.

```text
무엇을 만들어야 하지?
  └─ Question First

어떤 구조로 구현할까?
  └─ Architecture 또는 Design prompt

구현은 됐는데 놓친 조건이 없을까?
  └─ Senior Review 또는 Failure Analysis

다음에도 이 판단을 쓸 수 있을까?
  └─ Case 또는 Checklist로 정리
```

프롬프트가 결정을 대신해 주는 것은 아니다. 내가 놓친 전제와 위험을 찾고, 실제 코드와 테스트로 다시 확인하기 위해 사용한다.

## 무엇을 기록하나

- 요구사항에서 실제로 중요했던 제약
- 선택지를 비교한 과정과 최종 선택 이유
- 동시 요청, 재시도, 부분 실패처럼 정상 화면만 봐서는 알기 어려웠던 문제
- 테스트, 로그, 측정으로 확인한 결과
- 다음 프로젝트에서는 먼저 확인해야 할 질문

검색하면 바로 나오는 기술 정의나 직접 확인하지 않은 내용은 굳이 옮기지 않는다. 프로젝트의 사건을 그대로 복사하기보다, 그 경험에서 다음에도 사용할 수 있는 판단만 남긴다.

## 정리된 사례

- [업무 완료 상태는 검증된 전달 결과와 연결](cases/ticket-to-deployment-traceability.md)
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

## 새 경험을 추가할 때

먼저 프로젝트의 `context/playbook-export.md`에 검증된 후보를 한 건 적는다. 상세한 사건 기록과 로그는 원래 프로젝트에 두고, 이 저장소에는 다른 프로젝트에서도 다시 사용할 수 있는 판단만 옮긴다.

추가하기 전에는 기존 문서와 겹치지 않는지, 공개하면 안 되는 정보가 남아 있지 않은지 확인한다. 자세한 기준은 [AGENTS.md](AGENTS.md)에 정리되어 있다.
