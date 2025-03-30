```
symlink(target::AbstractString, link::AbstractString; dir_target = false)
```

创建一个指向 `target` 的符号链接，名称为 `link`。

在 Windows 上，符号链接必须明确声明是指向目录还是其他。如果 `target` 已经存在，默认情况下 `link` 的类型将被自动检测，然而如果 `target` 不存在，则此函数默认创建一个文件符号链接，除非将 `dir_target` 设置为 `true`。请注意，如果用户设置了 `dir_target` 但 `target` 存在且是一个文件，仍然会创建一个目录符号链接，但解引用该符号链接将失败，就像用户创建一个文件符号链接（通过在目录创建之前调用 `symlink()` 并将 `dir_target` 设置为 `false`）并尝试将其解引用为目录一样。

此外，在 Windows 上有两种创建链接的方法；符号链接和连接点。连接点稍微高效一些，但不支持相对路径，因此如果请求相对目录符号链接（如 `isabspath(target)` 返回 `false` 所示），将使用符号链接，否则将使用连接点。在 Windows 上创建符号链接的最佳实践是在引用的文件/目录已经创建后再创建它们。

另请参见: [`hardlink`](@ref)。

!!! note
    在不支持软符号链接的操作系统（如 Windows XP）下，此函数会引发错误。


!!! compat "Julia 1.6"
    `dir_target` 关键字参数是在 Julia 1.6 中添加的。在此之前，指向不存在路径的符号链接在 Windows 上总是文件符号链接，并且不支持指向目录的相对符号链接。

