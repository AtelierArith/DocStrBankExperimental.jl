```
LibGit2.map(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), range::AbstractString="", by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

使用 [`GitRevWalker`](@ref) `walker` 在仓库历史中“遍历”每个提交，将 `f` 应用到遍历中的每个提交。关键字参数包括：     * `oid`：要开始遍历的提交的 [`GitHash`](@ref)。默认使用       [`push_head!`](@ref)，因此使用 HEAD 提交及其所有祖先。     * `range`：格式为 `oid1..oid2` 的 `GitHash` 范围。`f` 将应用于两者之间的所有提交。     * `by`：排序方法。默认是不排序。其他选项包括按拓扑排序 (`LibGit2.Consts.SORT_TOPOLOGICAL`)、按时间向前排序 (`LibGit2.Consts.SORT_TIME`，最古老的在前) 或按时间向后排序 (`LibGit2.Consts.SORT_REVERSE`，最新的在前)。     * `rev`：是否反转排序顺序（例如，如果使用拓扑排序）。

# 示例

```julia
oids = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.map((oid, repo)->string(oid), walker, by=LibGit2.Consts.SORT_TIME)
end
```

在这里，`LibGit2.map` 使用 `GitRevWalker` 访问每个提交并找到其 `GitHash`。
