```
LibGit2.DiffOptionsStruct
```

[`git_diff_options`](https://libgit2.org/libgit2/#HEAD/type/git_diff_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `flags`: 어떤 파일이 diff에 나타날지를 제어하는 플래그. 기본값은 `DIFF_NORMAL`입니다.
  * `ignore_submodules`: 서브모듈의 파일을 볼 것인지 여부. 기본값은 `SUBMODULE_IGNORE_UNSPECIFIED`로, 이는 서브모듈의 설정이 diff에 나타날지 여부를 제어함을 의미합니다.
  * `pathspec`: diff에 포함할 파일의 경로. 기본값은 저장소의 모든 파일을 사용하는 것입니다.
  * `notify_cb`: 파일 델타가 추가될 때 diff의 변경 사항을 사용자에게 알리는 선택적 콜백입니다.
  * `progress_cb`: diff 진행 상황을 표시하는 선택적 콜백입니다. libgit2 버전이 최소 0.24.0 이상일 때만 관련이 있습니다.
  * `payload`: `notify_cb` 및 `progress_cb`에 전달할 페이로드입니다.
  * `context_lines`: 헌크의 가장자리를 정의하는 데 사용되는 *변경되지 않은* 라인의 수입니다. 이는 헌크 앞뒤에 제공되는 컨텍스트를 위해 표시될 라인의 수이기도 합니다. 기본값은 3입니다.
  * `interhunk_lines`: 두 개의 별도 헌크 사이에 허용되는 최대 *변경되지 않은* 라인의 수입니다. 기본값은 0입니다.
  * `id_abbrev`: 인쇄할 축약된 [`GitHash`](@ref)의 길이를 설정합니다. 기본값은 `7`입니다.
  * `max_size`: blob의 최대 파일 크기입니다. 이 크기를 초과하면 이진 blob으로 처리됩니다. 기본값은 512 MB입니다.
  * `old_prefix`: diff의 한쪽에 오래된 파일을 배치할 가상 파일 디렉토리입니다. 기본값은 `"a"`입니다.
  * `new_prefix`: diff의 한쪽에 새로운 파일을 배치할 가상 파일 디렉토리입니다. 기본값은 `"b"`입니다.
