```
LibGit2.read_tree!(idx::GitIndex, tree::GitTree)
LibGit2.read_tree!(idx::GitIndex, treehash::AbstractGitHash)
```

트리 `tree` (또는 `idx`가 소유한 리포지토리에서 `treehash`가 가리키는 트리)를 인덱스 `idx`로 읽어옵니다. 현재 인덱스 내용은 대체됩니다.
