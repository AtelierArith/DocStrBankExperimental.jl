```
add!(repo::GitRepo, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
add!(idx::GitIndex, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
```

`files`로 지정된 경로의 모든 파일을 인덱스 `idx`(또는 `repo`의 인덱스)에 추가합니다. 파일이 이미 존재하는 경우, 인덱스 항목이 업데이트됩니다. 파일이 이미 존재하지 않는 경우, 인덱스에 새로 추가됩니다. `files`는 glob 패턴을 포함할 수 있으며, 이 경우 일치하는 파일이 추가됩니다(단, `INDEX_ADD_DISABLE_PATHSPEC_MATCH`가 설정되어 있지 않은 경우). 파일이 무시된 경우(`.gitignore` 또는 설정에서), 인덱스에서 이미 추적되고 있지 않는 한 *추가되지 않습니다*. 인덱스에서 이미 추적되고 있는 경우에는 *업데이트됩니다*. 키워드 인수 `flags`는 무시된 파일과 관련된 동작을 제어하는 비트 플래그 집합입니다:

  * `Consts.INDEX_ADD_DEFAULT` - 위에서 설명한 기본값입니다.
  * `Consts.INDEX_ADD_FORCE` - 기존의 무시 규칙을 무시하고, 이미 무시된 경우에도 파일을 인덱스에 강제로 추가합니다.
  * `Consts.INDEX_ADD_CHECK_PATHSPEC` - `INDEX_ADD_FORCE`와 동시에 사용할 수 없습니다. 디스크에 존재하는 `files`의 각 파일이 무시 목록에 없는지 확인합니다. 파일 중 하나라도 *무시*된 경우, 함수는 `EINVALIDSPEC`를 반환합니다.
  * `Consts.INDEX_ADD_DISABLE_PATHSPEC_MATCH` - glob 매칭을 끄고, `files`에 지정된 경로와 정확히 일치하는 파일만 인덱스에 추가합니다.
