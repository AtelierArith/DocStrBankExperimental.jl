```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

一个注释的 git 提交携带了关于如何查找它以及原因的信息，以便 rebase 或合并操作可以获得有关提交上下文的更多信息。例如，冲突文件包含有关合并中冲突的源/目标分支的信息。注释提交可以引用远程分支的顶端，例如当传递一个 [`FetchHead`](@ref) 时，或者引用使用 `GitReference` 描述的分支头。
