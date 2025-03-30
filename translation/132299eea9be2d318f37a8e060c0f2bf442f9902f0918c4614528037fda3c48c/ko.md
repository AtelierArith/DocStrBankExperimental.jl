```
LibGit2.StatusEntry
```

HEAD에 존재하는 파일과 인덱스 간의 차이점과 인덱스와 작업 디렉토리 간의 차이점을 제공합니다. `git_status_entry` 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `status`: 파일의 상태 플래그를 포함하며, 현재 상태인지 또는 인덱스나 작업 트리에서 어떤 방식으로 변경되었는지를 나타냅니다.
  * `head_to_index`: HEAD에 존재하는 파일과 인덱스 간의 차이점을 캡슐화하는 [`DiffDelta`](@ref)에 대한 포인터입니다.
  * `index_to_workdir`: 인덱스에 존재하는 파일과 [`workdir`](@ref) 간의 차이점을 캡슐화하는 `DiffDelta`에 대한 포인터입니다.
