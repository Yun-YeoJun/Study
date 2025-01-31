# GitHub Actions의 Event

- Push
- Pull Request
- Issue
- Issue comment
  - Issue comment는 default branch에서만 동작한다.
- Schedule

  - 5분 간격, 30분 간격의 작업은 드랍될 가능성이 있다.
  - 정해진 시간에 꼭 실행되어야 하는 작업은 GitHub Actions Schedule 기능을 사용하기에 적절하지 않다.

    ```yaml
    name: schedule-workflow
    on:
    schedule:
      - cron: "15 * * * *"

    jobs: ...
    ```

- Workflow dispatch

  - 수동으로 워크플로우를 트리거하는 방법이다.
  - default branch에서만 동작한다.
  - input 값을 넣을 수 있다.

  ```yaml
  name: workflow_dispatch
  on:
    workflow_dispatch:
      inputs:
        name:
          description: "set name"
          required: true
          default: "github-actions"
          type: string
        environment:
          description: "set env"
          required: true
          default: "dev"
          type: choice
          options:
            - dev
            - prod
  jobs: ...
  ```

- 다양한 이벤트

  - 여러 이벤트로 하나의 워크플로우를 트리거할 수 있다.

  ```yaml
  on:
    push:
    issues:
      types: [opened]
    workflow_dispatch:

  jobs: ...
  ```

# needs

- 하나의 워크 플로우에서 여러 개의 잡을 사용하는 경우, job 간에 종속성을 생성하는 키워드이다.
- 하나의 job이 다른 job 또는 여러 job이 완료될 때 실행되도록 설정할 때 사용한다.
- 즉 여러 job의 실행 순서를 조절하는 키워드이다.

# re-run

- 과거에 실행된 워크플로우를 재실행하는 기능이다.
- 성공, 실패 여부와 상관없이 재실행할 수 있다.
- 다시 실행하는 시점이 아니라 과거 트리거된 그 시점을 기준으로 다시 실행한다.
  - 파일을 수정하고 과거에 실행된 워크플로우를 re run 하면 수정한 내용이 반영되지 않는다.
