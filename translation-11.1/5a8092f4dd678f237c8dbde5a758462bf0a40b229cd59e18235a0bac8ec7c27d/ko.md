```
LibGit2.MergeOptions
```

[`git_merge_options`](https://libgit2.org/libgit2/#HEAD/type/git_merge_options) 구조체와 일치합니다.

필드는 다음을 나타냅니다:

  * `version`: 나중에 변경될 경우를 대비하여 사용 중인 구조체의 버전. 현재는 항상 `1`입니다.
  * `flags`: 병합 동작을 설명하는 플래그에 대한 `enum`. [`git_merge_flag_t`](https://github.com/libgit2/libgit2/blob/HEAD/include/git2/merge.h#L95)에서 정의됩니다. 해당하는 Julia enum은 `GIT_MERGE`이며 값은 다음과 같습니다:

      * `MERGE_FIND_RENAMES`: 공통 조상과 "우리" 또는 "그들" 측 사이에서 파일이 이름이 변경되었는지 감지합니다. 파일이 이름이 변경된 경우 병합을 허용합니다.
      * `MERGE_FAIL_ON_CONFLICT`: 충돌이 발견되면 해결을 시도하기보다는 즉시 종료합니다.
      * `MERGE_SKIP_REUC`: 병합 결과로 생성된 인덱스에 REUC 확장을 작성하지 않습니다.
      * `MERGE_NO_RECURSIVE`: 병합되는 커밋에 여러 병합 기반이 있는 경우, 기반을 재귀적으로 병합하려고 시도하기보다는 첫 번째 것을 사용합니다.
  * `rename_threshold`: 두 파일이 서로의 이름 변경으로 간주되기 위해 얼마나 유사해야 하는지를 나타냅니다. 이는 유사성의 백분율을 설정하는 정수입니다. 기본값은 50입니다.
  * `target_limit`: 이름 변경을 찾기 위해 비교할 최대 파일 수입니다. 기본값은 200입니다.
  * `metric`: 이름 변경 감지를 위해 두 파일 간의 유사성을 결정하는 데 사용할 선택적 사용자 정의 함수입니다.
  * `recursion_limit`: 새로운 가상 병합 기반을 구축하기 위해 수행할 공통 조상의 병합 수에 대한 상한선입니다. 기본값은 제한이 없습니다. 이 필드는 libgit2 버전 0.24.0 이상에서만 존재합니다.
  * `default_driver`: 양쪽 모두 변경된 경우 사용할 병합 드라이버입니다. 이 필드는 libgit2 버전 0.25.0 이상에서만 존재합니다.
  * `file_favor`: `text` 드라이버에 대한 충돌 파일 내용을 처리하는 방법입니다.

      * `MERGE_FILE_FAVOR_NORMAL`: 병합의 양쪽 모두 섹션에 변경 사항이 있는 경우, `git checkout`이 병합 파일을 생성하는 데 사용할 인덱스에 충돌을 기록합니다. 사용자는 이를 참조하여 충돌을 해결할 수 있습니다. 이것이 기본값입니다.
      * `MERGE_FILE_FAVOR_OURS`: 병합의 양쪽 모두 섹션에 변경 사항이 있는 경우, 인덱스에서 병합의 "우리" 측 버전을 사용합니다.
      * `MERGE_FILE_FAVOR_THEIRS`: 병합의 양쪽 모두 섹션에 변경 사항이 있는 경우, 인덱스에서 병합의 "그들" 측 버전을 사용합니다.
      * `MERGE_FILE_FAVOR_UNION`: 병합의 양쪽 모두 섹션에 변경 사항이 있는 경우, 인덱스에 넣을 파일에 양쪽의 각 고유한 줄을 포함합니다.
  * `file_flags`: 파일 병합에 대한 지침입니다.
