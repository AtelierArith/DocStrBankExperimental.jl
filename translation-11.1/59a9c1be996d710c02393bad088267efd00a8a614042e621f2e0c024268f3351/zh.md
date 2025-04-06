```
LibGit2.isdiff(repo::GitRepo, treeish::AbstractString, pathspecs::AbstractString=""; cached::Bool=false)
```

检查由 `treeish` 指定的树与工作树中的跟踪文件（如果 `cached=false`）或索引（如果 `cached=true`）之间是否存在任何差异。`pathspecs` 是差异选项的规范。

# 示例

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdiff(repo, "HEAD") # 应该是 false
open(joinpath(repo_path, new_file), "a") do f
    println(f, "这是我很酷的新文件")
end
LibGit2.isdiff(repo, "HEAD") # 现在是 true
```

等同于 `git diff-index <treeish> [-- <pathspecs>]`。
