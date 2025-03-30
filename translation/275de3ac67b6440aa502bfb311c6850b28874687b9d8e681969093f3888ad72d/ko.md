```
LibGit2.push_head!(w::GitRevWalker)
```

HEAD 커밋과 그 조상들을 [`GitRevWalker`](@ref) `w`에 푸시합니다. 이렇게 하면 HEAD와 모든 조상 커밋이 탐색 중에 만날 수 있도록 보장됩니다.
