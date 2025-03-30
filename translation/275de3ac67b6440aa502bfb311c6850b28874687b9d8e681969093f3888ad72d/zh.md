```
LibGit2.push_head!(w::GitRevWalker)
```

将 HEAD 提交及其祖先推送到 [`GitRevWalker`](@ref) `w`。这确保在遍历过程中会遇到 HEAD 及其所有祖先提交。
