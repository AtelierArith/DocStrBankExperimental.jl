```
merge_base(repo::GitRepo, one::AbstractString, two::AbstractString) -> GitHash
```

查找提交 `one` 和 `two` 之间的合并基（共同祖先）。`one` 和 `two` 可以都是字符串形式。返回合并基的 `GitHash`。
