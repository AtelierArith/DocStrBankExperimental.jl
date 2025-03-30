```
LibGit2.tag_create(repo::GitRepo, tag::AbstractString, commit; kwargs...)
```

저장소 `repo`에서 커밋 `commit`에 새로운 git 태그 `tag` (예: `"v0.5"`)를 생성합니다.

키워드 인자는 다음과 같습니다:

  * `msg::AbstractString=""`: 태그에 대한 메시지.
  * `force::Bool=false`: `true`인 경우, 기존 참조가 덮어씌워집니다.
  * `sig::Signature=Signature(repo)`: 태그 작성자의 서명.
