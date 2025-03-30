```
GitBlame(repo::GitRepo, path::AbstractString; options::BlameOptions=BlameOptions())
```

`path`에 있는 파일에 대한 `GitBlame` 객체를 생성하며, `repo`의 기록에서 얻은 변경 정보를 사용합니다. `GitBlame` 객체는 누가 파일의 어떤 부분을 언제, 어떻게 변경했는지를 기록합니다. `options`는 파일의 내용을 분리하는 방법과 조사할 커밋을 제어합니다 - 더 많은 정보는 [`BlameOptions`](@ref)를 참조하세요.
