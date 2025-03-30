```
LibGit2.RebaseOperation
```

리베이스 중 수행할 단일 지시사항/작업을 설명합니다. [`git_rebase_operation`](https://libgit2.org/libgit2/#HEAD/type/git_rebase_operation_t) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `optype`: 현재 수행 중인 리베이스 작업의 유형입니다. 옵션은 다음과 같습니다:

      * `REBASE_OPERATION_PICK`: 해당 커밋을 체리픽합니다.
      * `REBASE_OPERATION_REWORD`: 해당 커밋을 체리픽하지만, 프롬프트를 사용하여 메시지를 다시 작성합니다.
      * `REBASE_OPERATION_EDIT`: 해당 커밋을 체리픽하지만, 사용자가 커밋의 내용과 메시지를 편집할 수 있도록 허용합니다.
      * `REBASE_OPERATION_SQUASH`: 해당 커밋을 이전 커밋으로 스쿼시합니다. 두 커밋의 커밋 메시지가 병합됩니다.
      * `REBASE_OPERATION_FIXUP`: 해당 커밋을 이전 커밋으로 스쿼시합니다. 이전 커밋의 커밋 메시지만 사용됩니다.
      * `REBASE_OPERATION_EXEC`: 커밋을 체리픽하지 않습니다. 명령을 실행하고 명령이 성공적으로 종료되면 계속 진행합니다.
  * `id`: 이 리베이스 단계에서 작업 중인 커밋의 [`GitHash`](@ref)입니다.
  * `exec`: `REBASE_OPERATION_EXEC`가 사용되는 경우, 이 단계에서 실행할 명령입니다 (예: 각 커밋 후 테스트 스위트를 실행).
