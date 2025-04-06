```
ffmerge!(repo::GitRepo, ann::GitAnnotated)
```

将快速前进合并更改到当前 HEAD。这仅在 `ann` 所引用的提交是当前 HEAD 的后代时才可能（例如，如果从远程分支拉取更改，而该分支仅在本地分支的顶部之前）。
