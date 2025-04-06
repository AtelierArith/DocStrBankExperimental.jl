```
LibGit2.isdirty(repo::GitRepo, pathspecs::AbstractString=""; cached::Bool=false) -> Bool
```

检查工作树中（如果 `cached=false`）或索引中（如果 `cached=true`）是否有任何已跟踪文件的更改。`pathspecs` 是差异选项的规范。

# 示例

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdirty(repo) # 应该是 false
open(joinpath(repo_path, new_file), "a") do f
    println(f, "这是我很酷的新文件")
end
LibGit2.isdirty(repo) # 现在是 true
LibGit2.isdirty(repo, new_file) # 现在是 true
```

等同于 `git diff-index HEAD [-- <pathspecs>]`。
