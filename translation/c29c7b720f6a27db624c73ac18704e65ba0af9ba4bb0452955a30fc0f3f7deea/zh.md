```
GitBlame(repo::GitRepo, path::AbstractString; options::BlameOptions=BlameOptions())
```

构造一个 `GitBlame` 对象，用于 `path` 处的文件，使用从 `repo` 的历史中获取的变更信息。`GitBlame` 对象记录了谁在何时以何种方式更改了文件的哪些部分。`options` 控制如何分隔文件的内容以及要探测哪些提交 - 有关更多信息，请参见 [`BlameOptions`](@ref)。
