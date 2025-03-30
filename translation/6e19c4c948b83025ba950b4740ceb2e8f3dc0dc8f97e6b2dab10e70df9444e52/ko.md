```
LibGit2.CloneOptions
```

[`git_clone_options`](https://libgit2.org/libgit2/#HEAD/type/git_clone_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `checkout_opts`: 클론의 일환으로 원격 체크아웃을 수행하기 위한 옵션입니다.
  * `fetch_opts`: 클론의 일환으로 원격의 사전 체크아웃 페치를 수행하기 위한 옵션입니다.
  * `bare`: `0`이면 전체 원격 저장소를 클론합니다. 0이 아닌 경우, 저장소에 소스 파일의 로컬 복사본이 없는 베어 클론을 수행하며, [`gitdir`](@ref)와 [`workdir`](@ref)가 동일합니다.
  * `localclone`: 로컬 객체 데이터베이스를 클론할지 또는 페치를 수행할지를 나타내는 플래그입니다. 기본값은 git이 결정하도록 하는 것입니다. 로컬 클론에 대해 git 인식 전송을 사용하지 않지만, `file://`로 시작하는 URL에 대해서는 사용합니다.
  * `checkout_branch`: 체크아웃할 브랜치의 이름입니다. 빈 문자열인 경우, 원격의 기본 브랜치가 체크아웃됩니다.
  * `repository_cb`: 클론이 생성될 *새로운* 저장소를 만들기 위해 사용될 선택적 콜백입니다.
  * `repository_cb_payload`: 저장소 콜백에 대한 페이로드입니다.
  * `remote_cb`: 클론을 만들기 전에 [`GitRemote`](@ref)를 생성하는 데 사용되는 선택적 콜백입니다.
  * `remote_cb_payload`: 원격 콜백에 대한 페이로드입니다.
