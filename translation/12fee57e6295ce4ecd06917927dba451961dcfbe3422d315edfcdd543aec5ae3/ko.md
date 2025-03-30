```
LibGit2.BlameOptions
```

[`git_blame_options`](https://libgit2.org/libgit2/#HEAD/type/git_blame_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `flags`: `Consts.BLAME_NORMAL` 또는 `Consts.BLAME_FIRST_PARENT` 중 하나 (다른 blame 플래그는 아직 libgit2에 의해 구현되지 않았습니다).
  * `min_match_characters`: 변경 사항이 해당 커밋과 연관되기 위해 커밋에서 변경되어야 하는 최소 *영숫자* 문자 수. 기본값은 20입니다. `Consts.BLAME_*_COPIES` 플래그 중 하나가 사용될 경우에만 적용되며, libgit2는 아직 이를 구현하지 않았습니다.
  * `newest_commit`: 변경 사항을 살펴볼 최신 커밋의 [`GitHash`](@ref).
  * `oldest_commit`: 변경 사항을 살펴볼 가장 오래된 커밋의 [`GitHash`](@ref).
  * `min_line`: 블레임을 시작할 파일의 첫 번째 줄. 기본값은 `1`입니다.
  * `max_line`: 블레임을 적용할 파일의 마지막 줄. 기본값은 `0`, 즉 파일의 마지막 줄을 의미합니다.
