```
LibGit2.ProxyOptions
```

프록시를 통해 연결하기 위한 옵션입니다.

[`git_proxy_options`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전입니다. 현재는 항상 `1`입니다.
  * `proxytype`: 사용할 프록시 유형에 대한 `enum`입니다. [`git_proxy_t`](https://libgit2.org/libgit2/#HEAD/type/git_proxy_t)에서 정의됩니다. 해당하는 Julia enum은 `GIT_PROXY`이며 값은 다음과 같습니다:

      * `PROXY_NONE`: 프록시를 통해 연결을 시도하지 않습니다.
      * `PROXY_AUTO`: git 구성에서 프록시 구성을 알아내려고 시도합니다.
      * `PROXY_SPECIFIED`: 이 구조체의 `url` 필드에 제공된 URL을 사용하여 연결합니다.

    기본값은 프록시 유형을 자동으로 감지하는 것입니다.
  * `url`: 프록시의 URL입니다.
  * `credential_cb`: 원격 연결에 인증이 필요한 경우 호출될 콜백 함수에 대한 포인터입니다.
  * `certificate_cb`: 인증서 검증이 실패할 경우 호출될 콜백 함수에 대한 포인터입니다. 이를 통해 사용자가 계속 연결할지 여부를 결정할 수 있습니다. 함수가 `1`을 반환하면 연결이 허용됩니다. `0`을 반환하면 연결이 허용되지 않습니다. 음수 값을 사용하여 오류를 반환할 수 있습니다.
  * `payload`: 두 콜백 함수에 제공될 페이로드입니다.

# 예제

```julia-repl
julia> fo = LibGit2.FetchOptions(
           proxy_opts = LibGit2.ProxyOptions(url = Cstring("https://my_proxy_url.com")))

julia> fetch(remote, "master", options=fo)
```
