```
@githash_str -> AbstractGitHash
```

从给定字符串构造一个 git 哈希对象，如果字符串短于 40 个十六进制数字，则返回 `GitShortHash`，否则返回 `GitHash`。

# 示例

```jldoctest
julia> LibGit2.githash"d114feb74ce633"
GitShortHash("d114feb74ce633")

julia> LibGit2.githash"d114feb74ce63307afe878a5228ad014e0289a85"
GitHash("d114feb74ce63307afe878a5228ad014e0289a85")
```
