```
LibGit2.CheckoutOptions
```

[`git_checkout_options`](https://libgit2.org/libgit2/#HEAD/type/git_checkout_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `checkout_strategy`: 충돌을 처리하는 방법과 체크아웃/누락된 파일을 재생성할지 여부를 결정합니다.
  * `disable_filters`: 0이 아닌 경우, UNIX와 DOS 간의 파일 개행을 변환하는 CLRF와 같은 필터를 적용하지 않습니다.
  * `dir_mode`: 체크아웃에 관련된 모든 디렉토리에 대한 읽기/쓰기/접근 모드. 기본값은 `0755`입니다.
  * `file_mode`: 체크아웃에 관련된 모든 파일에 대한 읽기/쓰기/접근 모드. 기본값은 blob에 따라 `0755` 또는 `0644`입니다.
  * `file_open_flags`: 체크아웃 중에 파일을 열기 위해 사용되는 비트 플래그입니다.
  * `notify_flags`: 사용자에게 어떤 종류의 충돌에 대해 알릴지에 대한 플래그입니다.
  * `notify_cb`: 체크아웃 충돌이 발생할 경우 사용자에게 알리기 위한 선택적 콜백 함수입니다. 이 함수가 0이 아닌 값을 반환하면 체크아웃이 취소됩니다.
  * `notify_payload`: 알림 콜백 함수에 대한 페이로드입니다.
  * `progress_cb`: 체크아웃 진행 상황을 표시하기 위한 선택적 콜백 함수입니다.
  * `progress_payload`: 진행 콜백에 대한 페이로드입니다.
  * `paths`: 비어 있지 않은 경우 체크아웃 중 검색할 경로를 설명합니다. 비어 있으면 체크아웃은 리포지토리의 모든 파일에 대해 발생합니다.
  * `baseline`: [`workdir`](@ref)의 예상 내용으로, (포인터가 있는) [`GitTree`](@ref)에 캡처됩니다. 기본값은 HEAD에서의 트리 상태입니다.
  * `baseline_index`: [`workdir`](@ref)의 예상 내용으로, (포인터가 있는) `GitIndex`에 캡처됩니다. 기본값은 HEAD에서의 인덱스 상태입니다.
  * `target_directory`: 비어 있지 않은 경우, `workdir` 대신 이 디렉토리로 체크아웃합니다.
  * `ancestor_label`: 충돌이 발생할 경우, 공통 조상의 이름입니다.
  * `our_label`: 충돌이 발생할 경우, "우리" 측의 이름입니다.
  * `their_label`: 충돌이 발생할 경우, "그들" 측의 이름입니다.
  * `perfdata_cb`: 성능 데이터를 표시하기 위한 선택적 콜백 함수입니다.
  * `perfdata_payload`: 성능 콜백에 대한 페이로드입니다.
