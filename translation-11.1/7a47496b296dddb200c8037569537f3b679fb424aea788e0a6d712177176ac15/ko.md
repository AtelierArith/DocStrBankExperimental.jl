```
LibGit2.FetchHead
```

가져오기 중 HEAD에 대한 정보를 포함하며, 가져온 브랜치의 이름과 URL, HEAD의 oid, 가져온 HEAD가 로컬에 병합되었는지 여부를 포함합니다.

필드는 다음을 나타냅니다:

  * `name`: 가져오기 헤드의 로컬 참조 데이터베이스에서의 이름, 예를 들어,  `"refs/heads/master"`.
  * `url`: 가져오기 헤드의 URL.
  * `oid`: 가져오기 헤드의 끝 부분의 [`GitHash`](@ref).
  * `ismerge`: 원격의 변경 사항이 로컬 복사본에 병합되었는지 여부를 나타내는 부울 플래그입니다. `true`인 경우, 로컬 복사본은 원격 가져오기 헤드와 최신 상태입니다.
