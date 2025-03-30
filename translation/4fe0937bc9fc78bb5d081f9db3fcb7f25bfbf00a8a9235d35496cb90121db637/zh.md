```
commit(repo::GitRepo, msg::AbstractString; kwargs...) -> GitHash
```

包装 [`git_commit_create`](https://libgit2.org/libgit2/#HEAD/group/commit/git_commit_create)。在仓库 `repo` 中创建一个提交。`msg` 是提交信息。返回新提交的 OID。

关键字参数包括：

  * `refname::AbstractString=Consts.HEAD_FILE`：如果不为 NULL，则更新指向新提交的引用名称。例如，`"HEAD"` 将更新当前分支的 HEAD。如果引用尚不存在，将会被创建。
  * `author::Signature = Signature(repo)` 是一个 `Signature`，包含有关提交作者的信息。
  * `committer::Signature = Signature(repo)` 是一个 `Signature`，包含有关将提交提交到仓库的人的信息。不一定与 `author` 相同，例如，如果 `author` 将补丁通过电子邮件发送给 `committer`，然后由 `committer` 提交。
  * `tree_id::GitHash = GitHash()` 是一个 git 树，用于创建提交，显示其祖先及与其他历史的关系。`tree` 必须属于 `repo`。
  * `parent_ids::Vector{GitHash}=GitHash[]` 是一个由 [`GitHash`](@ref) 组成的提交列表，用作新提交的父提交，可以为空。如果是合并提交，提交可能有多个父提交。
