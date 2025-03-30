```
LibGit2.count(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

使用 [`GitRevWalker`](@ref) `walker` 在仓库历史中“遍历”每个提交，找到当 `f` 应用于它们时返回 `true` 的提交数量。关键字参数包括：     * `oid`：要开始遍历的提交的 [`GitHash`](@ref)。默认使用       [`push_head!`](@ref)，因此从 HEAD 提交及其所有祖先开始。     * `by`：排序方法。默认是不排序。其他选项包括按拓扑排序 (`LibGit2.Consts.SORT_TOPOLOGICAL`)、按时间向前排序 (`LibGit2.Consts.SORT_TIME`，最古老的在前) 或按时间向后排序 (`LibGit2.Consts.SORT_REVERSE`，最新的在前)。     * `rev`：是否反转排序顺序（例如，如果使用拓扑排序）。

# 示例

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid, repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

`LibGit2.count` 找到沿着某个 `GitHash` `commit_oid1` 的遍历中的提交数量，从该提交开始遍历并向前移动。由于 `GitHash` 对于每个提交是唯一的，`cnt` 将为 `1`。
