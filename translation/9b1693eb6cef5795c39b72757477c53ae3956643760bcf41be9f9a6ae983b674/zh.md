```
mktemp(parent=tempdir(); cleanup=true) -> (path, io)
```

返回 `(path, io)`，其中 `path` 是 `parent` 中新临时文件的路径，`io` 是该路径的打开文件对象。`cleanup` 选项控制临时文件在进程退出时是否自动删除。

!!! compat "Julia 1.3"
    `cleanup` 关键字参数是在 Julia 1.3 中添加的。相关地，从 1.3 开始，Julia 会在 Julia 进程退出时删除由 `mktemp` 创建的临时路径，除非 `cleanup` 被显式设置为 `false`。

