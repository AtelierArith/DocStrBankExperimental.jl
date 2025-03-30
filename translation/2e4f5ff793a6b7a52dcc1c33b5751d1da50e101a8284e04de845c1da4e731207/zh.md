```
edit(function, [types])
edit(module)
```

编辑函数的定义，选项上可以指定一个类型元组以指示要编辑哪个方法。对于模块，打开主源文件。模块需要先通过 `using` 或 `import` 加载。

!!! compat "Julia 1.1"
    对模块使用 `edit` 至少需要 Julia 1.1。


为了确保可以在给定行打开文件，您可能需要先调用 `InteractiveUtils.define_editor`。
