```
committer(c::GitCommit)
```

커밋 `c`의 커미터의 `Signature`를 반환합니다. 커미터는 원래 [`author`](@ref)로 작성된 변경 사항을 커밋한 사람이며, `author`와 동일할 필요는 없습니다. 예를 들어, `author`가 패치를 이메일로 보내고 이를 커밋한 `committer`가 있을 수 있습니다.
