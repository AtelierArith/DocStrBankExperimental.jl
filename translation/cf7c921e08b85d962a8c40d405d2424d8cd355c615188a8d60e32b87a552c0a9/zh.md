```
dlopen(libfile::AbstractString [, flags::Integer]; throw_error:Bool = true)
```

加载共享库，返回一个不透明的句柄。

常量 `dlext`（`.so`、`.dll` 或 `.dylib`）给出的扩展可以从 `libfile` 字符串中省略，因为如果需要，它会自动附加。如果 `libfile` 不是绝对路径名，则会在数组 `DL_LOAD_PATH` 中搜索 `libfile`，然后是系统加载路径。

可选的 flags 参数是 `RTLD_LOCAL`、`RTLD_GLOBAL`、`RTLD_LAZY`、`RTLD_NOW`、`RTLD_NODELETE`、`RTLD_NOLOAD`、`RTLD_DEEPBIND` 和 `RTLD_FIRST` 的按位或。这些会被转换为 POSIX（和/或 GNU libc 和/或 MacOS）dlopen 命令的相应标志（如果可能），或者在当前平台上如果指定的功能不可用则被忽略。默认标志是平台特定的。在 MacOS 上，默认的 `dlopen` 标志是 `RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL`，而在其他平台上，默认是 `RTLD_LAZY|RTLD_DEEPBIND|RTLD_LOCAL`。这些标志的重要用途是指定动态库加载器在将库引用绑定到导出符号时的非默认行为，以及绑定的引用是放入进程本地还是全局范围。例如，`RTLD_LAZY|RTLD_DEEPBIND|RTLD_GLOBAL` 允许库的符号在其他共享库中可用，解决共享库之间存在依赖关系的情况。

如果找不到库，此方法会抛出错误，除非关键字参数 `throw_error` 被设置为 `false`，在这种情况下，此方法返回 `nothing`。

!!! note
    从 Julia 1.6 开始，此方法将以 `@executable_path/` 开头的路径替换为 Julia 可执行文件的路径，允许可重定位的相对路径加载。在 Julia 1.5 及更早版本中，这仅在 macOS 上有效。

