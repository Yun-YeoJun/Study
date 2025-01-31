# GitHub Actions 란?

- GitHub의 자동화 도구
- 소프트웨어 개발 워크플로우를 자동화할 때 사용할 수 있다.
- YAML을 사용하여 워크플로우를 쉽게 사용할 수 있다. (.yml, .yaml)
- GitHub의 다양한 이벤트에 따라 워크플로우를 실행할 수 있다.

# GitHub Actions 컴포넌트

- workflow
  - 하나 이상의 작업을 실행하는 구성 가능한 자동화 프로세스이다.
  - `.github/workflows` 경로에 파일이 있어야 실행된다.
  - 여러 워크플로우를 생성하고 사용할 수 있다.
- event
  - 워크플로우의 실행을 트리거하는 GitHub Repository 내 특정 활동이다.
    - 워크플로우 트리거 방식
      - Repository 내 이벤트 기반 (push, pull request, ...)
      - 수동
      - 스케줄
      - Repository 외부
- runner
  - job을 실행할 수 있는 서버이다.
  - 각 러너는 하나의 job을 실행한다.
  - Linux, Windows, macOS 지원한다.
- job
  - 러너에서 실행되는 step의 집합이다.
  - 액션과 스크립트 등을 step에 정의해서 사용한다.
  - 기본적으로 각 job은 병렬로 실행된다.
    - job을 순차적으로 실행하려면 `needs`를 사용한다.
- step
  - job이 실행하는 개별 명령이다.
  - step은 순차적으로 실행되며, 한 step이 실패하면 그 다음 step부터 실행되지 않는다.
- action
  - 특정 작업을 수행하는 코드 조각이다.
  - `uses` 키워드를 이용해서 action을 로드할 수 있다.
  - 하나의 step에서 하나의 action만 가능하다.
  - 종류
    - GitHub 공식 제공 action
    - GitHub Community에서 만든 action
    - 사용자가 직접 만든 action
  - GitHub Marketplace
    - 액션 저장소이다.
    - 커스텀 액션을 업로드할 수 있다.
    - 다른 사용자가 만든 액션을 사용할 수 있다.
