```
LibGit2.revcount(repo::GitRepo, commit1::AbstractString, commit2::AbstractString)
```

列出 `commit1` 和 `commit2` 之间的修订次数（以字符串形式表示的提交 OID）。由于 `commit1` 和 `commit2` 可能位于不同的分支上，`revcount` 执行“左-右”修订列表（和计数），返回一个 `Int` 的元组 - 左侧和右侧提交的数量。左（或右）提交指的是从树的对称差异的哪一侧可以到达该提交。

等同于 `git rev-list --left-right --count <commit1> <commit2>`。

# 示例

```julia
repo = LibGit2.GitRepo(repo_path)
repo_file = open(joinpath(repo_path, test_file), "a")
println(repo_file, "hello world")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid1 = LibGit2.commit(repo, "commit 1")
println(repo_file, "hello world again")
flush(repo_file)
LibGit2.add!(repo, test_file)
commit_oid2 = LibGit2.commit(repo, "commit 2")
LibGit2.revcount(repo, string(commit_oid1), string(commit_oid2))
```

这将返回 `(-1, 0)`。
