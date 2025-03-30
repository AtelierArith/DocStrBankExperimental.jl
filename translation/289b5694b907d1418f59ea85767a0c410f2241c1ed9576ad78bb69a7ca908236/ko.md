```
GitTag(repo::GitRepo, hash::AbstractGitHash)
GitTag(repo::GitRepo, spec::AbstractString)
```

`hash`/`spec`로 지정된 `repo`에서 `GitTag` 객체를 반환합니다.

  * `hash`는 전체(`GitHash`) 또는 부분(`GitShortHash`) 해시입니다.
  * `spec`은 텍스트 사양입니다: 전체 목록은 [git 문서](https://git-scm.com/docs/git-rev-parse.html#_specifying_revisions)를 참조하십시오.
