```
LibGit2.PushOptions
```

[`git_push_options`](https://libgit2.org/libgit2/#HEAD/type/git_push_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전입니다. 현재는 항상 `1`입니다.
  * `parallelism`: 패킷 파일을 생성해야 하는 경우, 이 변수는 패킷 빌더에 의해 생성될 작업자 스레드의 수를 설정합니다. `0`인 경우, 패킷 빌더는 사용할 스레드 수를 자동으로 설정합니다. 기본값은 `1`입니다.
  * `callbacks`: 푸시를 위해 사용할 콜백(예: 원격 인증용)입니다.
  * `proxy_opts`: LibGit2 버전이 `0.25.0` 이상인 경우에만 관련이 있습니다. 원격과 통신하기 위해 프록시를 사용하는 옵션을 설정합니다. 자세한 내용은 [`ProxyOptions`](@ref)를 참조하십시오.
  * `custom_headers`: LibGit2 버전이 `0.24.0` 이상인 경우에만 관련이 있습니다. 푸시 작업에 필요한 추가 헤더입니다.
