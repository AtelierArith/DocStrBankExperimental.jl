```
add!(repo::GitRepo, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
add!(idx::GitIndex, files::AbstractString...; flags::Cuint = Consts.INDEX_ADD_DEFAULT)
```

将所有由 `files` 指定路径的文件添加到索引 `idx`（或 `repo` 的索引）。如果文件已经存在，索引条目将被更新。如果文件尚不存在，它将被新添加到索引中。`files` 可能包含将被扩展的通配符模式，任何匹配的文件将被添加（除非设置了 `INDEX_ADD_DISABLE_PATHSPEC_MATCH`，见下文）。如果文件被忽略（在 `.gitignore` 或配置中），它 *将不会* 被添加，*除非* 它已经在索引中被跟踪，在这种情况下它 *将* 被更新。关键字参数 `flags` 是一组位标志，用于控制与被忽略文件相关的行为：

  * `Consts.INDEX_ADD_DEFAULT` - 默认，如上所述。
  * `Consts.INDEX_ADD_FORCE` - 忽略现有的忽略规则，强制将文件添加到索引，即使它已经被忽略。
  * `Consts.INDEX_ADD_CHECK_PATHSPEC` - 不能与 `INDEX_ADD_FORCE` 同时使用。检查 `files` 中每个存在于磁盘上的文件是否不在忽略列表中。如果其中一个文件 *被* 忽略，函数将返回 `EINVALIDSPEC`。
  * `Consts.INDEX_ADD_DISABLE_PATHSPEC_MATCH` - 关闭通配符匹配，仅添加与 `files` 中指定路径完全匹配的文件到索引。
