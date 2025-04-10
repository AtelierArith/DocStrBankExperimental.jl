```
tempname(parent=tempdir(); cleanup=true) -> String
```

生成一个临时文件路径。此函数仅返回一个路径；不会创建文件。该路径可能是唯一的，但由于两个同时调用 `tempname` 生成相同文件名的可能性非常小，因此无法保证。该名称保证与调用 `tempname` 时已存在的所有文件不同。

当不带参数调用时，临时名称将是系统临时目录中临时名称的绝对路径，如 `tempdir()` 所示。如果提供了 `parent` 目录参数，则临时路径将位于该目录中。

`cleanup` 选项控制进程在退出时是否尝试自动删除返回的路径。请注意，`tempname` 函数不会在返回的位置创建任何文件或目录，因此除非您在该位置创建文件或目录，否则没有任何内容需要清理。如果您这样做并且 `cleanup` 为 `true`，则在进程终止时将被删除。

!!! compat "Julia 1.4"
    `parent` 和 `cleanup` 参数是在 1.4 中添加的。在 Julia 1.4 之前，`tempname` 的路径在进程终止时永远不会被清理。


!!! warning
    如果另一个进程获得相同的文件名并在您能够之前创建该文件，这可能会导致安全漏洞。如果这是一个问题，请使用 `JL_O_EXCL` 打开文件。也建议使用 [`mktemp()`](@ref)。

