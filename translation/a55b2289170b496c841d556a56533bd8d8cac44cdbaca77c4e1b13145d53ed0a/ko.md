```
LibGit2.push!(w::GitRevWalker, cid::GitHash)
```

[`GitRevWalker`](@ref) `walker`를 커밋 `cid`에서 시작합니다. 이 함수는 특정 연도 이후의 모든 커밋에 함수를 적용하는 데 사용할 수 있으며, 해당 연도의 첫 번째 커밋을 `cid`로 전달한 다음 결과로 얻은 `w`를 [`LibGit2.map`](@ref)에 전달하면 됩니다.
