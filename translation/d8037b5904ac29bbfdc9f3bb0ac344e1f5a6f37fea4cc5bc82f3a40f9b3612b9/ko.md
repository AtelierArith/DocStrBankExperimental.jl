```
LibGit2.DiffDelta
```

하나의 항목에 대한 변경 사항 설명. [`git_diff_delta`](https://libgit2.org/libgit2/#HEAD/type/git_diff_delta) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `status`: 파일이 추가/수정/삭제되었는지를 나타내는 `Consts.DELTA_STATUS` 중 하나.
  * `flags`: 델타 및 양쪽 객체에 대한 플래그. 파일을 이진/텍스트로 처리할지, 델타의 양쪽에 존재하는지, 객체 ID가 올바른지 여부를 결정합니다.
  * `similarity`: 파일이 이름이 변경되었거나 복사되었는지를 나타내는 데 사용됩니다.
  * `nfiles`: 델타에 있는 파일 수(예: 델타가 서브모듈 커밋 ID에서 실행된 경우, 하나 이상의 파일이 포함될 수 있습니다).
  * `old_file`: 변경 사항 이전의 파일에 대한 정보를 포함하는 [`DiffFile`](@ref).
  * `new_file`: 변경 사항 이후의 파일에 대한 정보를 포함하는 [`DiffFile`](@ref).
