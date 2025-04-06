```
LibGit2.FetchOptions
```

[`git_fetch_options`](https://libgit2.org/libgit2/#HEAD/type/git_fetch_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `callbacks`: 가져오는 동안 사용할 원격 콜백.
  * `prune`: 가져온 후에 가지치기를 수행할지 여부. 기본값은 `GitConfig`의 설정을 사용하는 것입니다.
  * `update_fetchhead`: 가져온 후에 [`FetchHead`](@ref)를 업데이트할지 여부. 기본값은 업데이트를 수행하는 것으로, 이는 일반적인 git 동작입니다.
  * `download_tags`: 원격에 존재하는 태그를 다운로드할지 여부. 기본값은 서버에서 다운로드되는 객체에 대해 태그를 요청하는 것입니다.
  * `proxy_opts`: 프록시를 통해 원격에 연결하기 위한 옵션. [`ProxyOptions`](@ref)를 참조하십시오. libgit2 버전이 0.25.0 이상인 경우에만 존재합니다.
  * `custom_headers`: 가져오기에 필요한 추가 헤더. libgit2 버전이 0.24.0 이상인 경우에만 존재합니다.
