```
LibGit2.push!(w::GitRevWalker, cid::GitHash)
```

从提交 `cid` 开始 [`GitRevWalker`](@ref) `walker`。此函数可用于对自某一年以来的所有提交应用一个函数，通过将该年的第一个提交作为 `cid` 传递，然后将结果 `w` 传递给 [`LibGit2.map`](@ref)。
