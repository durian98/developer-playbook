# Engineering Playbook

> 기술을 정리하는 저장소가 아니다. 프로젝트를 진행하며 얻은 **설계 판단**, **실패 사례**, **트레이드오프**, **AI 활용법**, **엔지니어링 사고방식**을 기록하는 저장소이다.

## 목적

검색하면 나오는 기술 지식을 저장하지 않는다. 프로젝트 경험을 통해 얻은 재사용 가능한 사고와 판단 기준을 축적한다.

AI는 초안과 구현을 빠르게 만들 수 있지만, 정상 흐름에서 동작하는 코드가 운영 환경에서도 안전한지는 별개의 문제다. 이 플레이북은 다음 질문에 답하는 기록이 된다.

- 왜 이 구조와 기술을 선택했는가?
- 어떤 불변조건이 깨지면 안 되는가?
- 동시 요청, 중복 요청, 부분 실패에서 어떻게 망가질 수 있는가?
- 대안은 무엇이며 현재 프로젝트 규모에서는 어디까지가 적절한가?
- AI를 코드 생성기가 아니라 설계 멘토·가상 공격자·학습 파트너로 어떻게 썼는가?

목표는 몇 년 뒤 기술 설명을 찾는 노트가 아니라, **왜 그때 그런 판단을 했는지** 되짚을 수 있는 기록을 만드는 것이다. 가장 먼저 읽을 문서는 [Question First](mindset/question-first.md)다.

## 핵심 원칙

상세 원칙의 원본은 [Engineering Philosophy](mindset/engineering-philosophy.md)이며, README에는 방향만 요약한다.

1. AI로 최소 구현을 빠르게 만든 뒤, 핵심 위험만 깊게 검증한다.
2. 정상 동작만으로 안전하다고 결론 내리지 않는다.
3. 선택의 근거, 트레이드오프, 운영상의 영향을 남긴다.

## 문서 구조

```text
developer-playbook/
├── README.md
├── mindset/
│   ├── question-first.md
│   ├── engineering-philosophy.md
│   └── ai-workflow.md
├── prompts/
│   ├── architecture.md
│   ├── design.md
│   ├── review.md
│   ├── failure-analysis.md
│   ├── learning.md
│   ├── retrospective.md
│   └── search.md
├── checklists/
├── failure-patterns/
├── templates/
└── cases/
```

각 폴더는 아래 역할만 맡는다. 같은 내용을 여러 폴더에 전문으로 복사하지 않는다.

- [Mindset](mindset/question-first.md): 질문하는 방식, 개발 철학, AI와의 작업 흐름
- [Prompts](prompts/): 프로젝트 단계별 AI 활용 프롬프트
- [Checklists](checklists/): 구현 전후 반복 확인할 질문
- [Failure Patterns](failure-patterns/): 실패가 드러나는 조건과 재현 관점
- [Templates](templates/): 프로젝트 경험을 플레이북으로 승격하는 양식
- [Cases](cases/): 검증된 실제 사례와 설계 판단

## 기록 기준

기록하지 않는 것:

- 검색으로 바로 찾을 수 있는 기술 정의와 문법
- 사용해 보지 않은 패턴의 요약
- 근거 없는 "항상 이렇게 해야 한다"는 규칙

기록하는 것:

- 문제, 조건, 선택지, 결정과 근거
- 발견하지 못했던 맹점과 재현 방법
- 개선 전후의 측정·테스트·관찰 결과
- 다음 프로젝트에도 쓸 수 있는 질문

## 사례 문서 최소 템플릿

```md
# 제목

## 맥락
프로젝트 규모, 제약, 요구사항.

## 불변조건
절대 깨지면 안 되는 사실.

## 문제와 재현
실패가 일어나는 정확한 순서와 확인 방법.

## 대안과 결정
비교한 선택지, 선택 이유, 감수한 트레이드오프.

## 검증
테스트, 로그, 지표, 실행계획 등 근거.

## 다음에 확인할 질문
이번 경험에서 얻은 재사용 가능한 질문.
```

## 사용하는 흐름

1. 기능의 목적과 불변조건을 짧게 적는다.
2. AI와 함께 가장 단순한 구현과 대안을 비교한다.
3. 실패 시나리오로 동시성·중복·부분 실패·권한 문제를 먼저 드러낸다.
4. 실제로 중요한 위험만 테스트 또는 측정으로 검증한다.
5. 선택과 남은 위험을 사례 문서에 짧게 남긴다.

프롬프트는 정답을 대신 고르는 지침이 아니다. 생각을 넓히고, 확인해야 할 가정을 드러내기 위한 도구다.

```text
요구사항 → Architecture Review → Design Review → 구현 → Senior Review
→ Failure Analysis → 회고 → Playbook Export → Playbook 업데이트
```

## 현재 사례

- [테스트 실행 환경과 이미지 빌드 책임 분리](cases/ci-test-and-image-build-boundary.md)
- [이벤트 수신 범위와 빌드 대상 분리](cases/webhook-trigger-and-build-scope.md)

## 프로젝트에서 승격하는 방법

프로젝트의 `context/playbook-export.md`에 검증된 후보 한 건을 먼저 남긴다. 이후 후보를 지정해 `developer-playbook` 반영을 요청하면, 중복·민감정보를 검토한 뒤 적절한 기존 문서를 수정하거나 새 문서 하나를 추가한다. 실제 프로젝트 기록은 이 저장소에 복사하지 않으며, 커밋과 푸시는 별도 요청이 있을 때만 수행한다.
