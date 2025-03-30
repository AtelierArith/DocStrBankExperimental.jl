```
LibGit2.StatusOptions
```

`git_status_foreach_ext()`가 콜백을 발행하는 방식을 제어하는 옵션입니다. [`git_status_opt_t`](https://libgit2.org/libgit2/#HEAD/type/git_status_opt_t) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전입니다. 현재는 항상 `1`입니다.
  * `show`: 어떤 파일을 검사할지와 그 순서를 나타내는 플래그입니다. 기본값은 `Consts.STATUS_SHOW_INDEX_AND_WORKDIR`입니다.
  * `flags`: 상태 호출에 사용되는 콜백을 제어하는 플래그입니다.
  * `pathspec`: 경로 일치를 위해 사용할 경로의 배열입니다. 경로 일치의 동작은 `show`와 `flags`의 값에 따라 달라집니다.
  * `baseline`: 작업 디렉토리와 인덱스와 비교하는 데 사용될 트리입니다; 기본값은 HEAD입니다.
