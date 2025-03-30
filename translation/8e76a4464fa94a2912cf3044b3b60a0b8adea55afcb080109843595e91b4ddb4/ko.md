```
LibGit2.DiffFile
```

델타의 한 쪽에 대한 설명. [`git_diff_file`](https://libgit2.org/libgit2/#HEAD/type/git_diff_file) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `id`: diff에서 항목의 [`GitHash`](@ref). 이 diff의 이 쪽에서 항목이 비어 있는 경우(예: 파일 제거의 diff인 경우), 이는 `GitHash(0)`이 됩니다.
  * `path`: 리포지토리의 작업 디렉토리에 상대적인 항목에 대한 `NULL`로 종료된 경로.
  * `size`: 항목의 크기(바이트 단위).
  * `flags`: [`git_diff_flag_t`](https://libgit2.org/libgit2/#HEAD/type/git_diff_flag_t) 플래그의 조합. 이 정수의 `i`번째 비트는 `i`번째 플래그를 설정합니다.
  * `mode`: 항목에 대한 [`stat`](@ref) 모드.
  * `id_abbrev`: `0.25.0` 이상 버전의 LibGit2에서만 존재합니다. [`string`](@ref)으로 변환할 때 `id` 필드의 길이. 일반적으로 `OID_HEXSZ`(40)와 같습니다.
