```
LibGit2.DescribeFormatOptions
```

[`git_describe_format_options`](https://libgit2.org/libgit2/#HEAD/type/git_describe_format_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `abbreviated_size`: 사용할 약어 `GitHash`의 크기에 대한 하한, 기본값은 `7`입니다.
  * `always_use_long_format`: 짧은 형식을 사용할 수 있는 경우에도 문자열에 긴 형식을 사용하려면 `1`로 설정합니다.
  * `dirty_suffix`: 설정된 경우, [`workdir`](@ref)가 더럽혀져 있으면 설명 문자열의 끝에 추가됩니다.
