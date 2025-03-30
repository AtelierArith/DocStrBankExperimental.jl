```
LibGit2.DescribeOptions
```

[`git_describe_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `max_candidates_tags`: 커밋을 설명하기 위해 `refs/tags`에서 가장 최근의 태그를 이만큼 고려합니다. 기본값은 10입니다(즉, 가장 최근의 10개 태그가 커밋을 설명하는지 확인됩니다).
  * `describe_strategy`: `refs/tags`의 모든 항목을 고려할지(`git-describe --tags`와 동등) 또는 `refs/`의 모든 항목을 고려할지(`git-describe --all`과 동등) 여부. 기본값은 주석이 달린 태그만 표시하는 것입니다. `Consts.DESCRIBE_TAGS`가 전달되면 주석이 달린 태그와 상관없이 모든 태그가 고려됩니다. `Consts.DESCRIBE_ALL`이 전달되면 `refs/`의 모든 참조가 고려됩니다.
  * `pattern`: `pattern`과 일치하는 태그만 고려합니다. 글로브 확장을 지원합니다.
  * `only_follow_first_parent`: 일치하는 참조에서 설명된 객체까지의 거리를 찾을 때, 첫 번째 부모로부터의 거리만 고려합니다.
  * `show_commit_oid_as_fallback`: 커밋을 설명하는 일치하는 참조를 찾을 수 없는 경우, 오류를 발생시키는 대신 커밋의 [`GitHash`](@ref)를 표시합니다(기본 동작).
