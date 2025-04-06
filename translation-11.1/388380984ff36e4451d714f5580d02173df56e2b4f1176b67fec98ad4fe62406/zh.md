```
arg_writers([ type = ArgWrite ]) do path::String, arg::Function
    ## 测试前设置 ##
    @arg_test arg begin
        arg :: ArgWrite
        ## 使用 `arg` 进行测试 ##
    end
    ## 测试后清理 ##
end
```

`arg_writers` 函数接受一个 do 块，该块对于 `arg_write` 可以处理的每种测试写入器类型被调用一次，使用一个临时（不存在的）`path` 和可以转换为各种可写参数类型的 `arg`，这些参数写入到 `path`。如果提供了可选的 `type` 参数，则仅对生成该类型参数的写入器调用 do 块。

传递给 do 块的 `arg` 不是参数值本身，因为某些测试参数类型需要为每个测试用例进行初始化和最终化。考虑一个打开的文件句柄参数：一旦你在一个测试中使用了它，就不能再使用它；你需要关闭它并为下一个测试重新打开文件。这个函数 `arg` 可以使用 `@arg_test arg begin ... end` 转换为 `ArgWrite` 实例。

还有一个 `arg_writers` 方法，它接受一个路径名称，类似于 `arg_readers`：

```
arg_writers(path::AbstractString, [ type = ArgWrite ]) do arg::Function
    ## 测试前设置 ##
    @arg_test arg begin
        # 这里 `arg :: ArgWrite`
        ## 使用 `arg` 进行测试 ##
    end
    ## 测试后清理 ##
end
```

如果你需要指定 `path` 而不是使用 `tempname()` 生成的路径名称，这个方法是有用的。由于 `path` 是从 `arg_writers` 外部传递的，因此在这种形式中，路径不是 do 块的参数。
