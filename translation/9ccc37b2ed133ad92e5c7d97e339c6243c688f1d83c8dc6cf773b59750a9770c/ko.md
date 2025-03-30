```
GitObject(repo::GitRepo, hash::AbstractGitHash)
GitObject(repo::GitRepo, spec::AbstractString)
```

지정된 객체([`GitCommit`](@ref), [`GitBlob`](@ref), [`GitTree`](@ref) 또는 [`GitTag`](@ref))를 `hash`/`spec`으로 지정된 `repo`에서 반환합니다.

  * `hash`는 전체(`GitHash`) 또는 부분(`GitShortHash`) 해시입니다.
  * `spec`은 텍스트 사양입니다: 전체 목록은 [git 문서](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions)를 참조하십시오.
