```
arg_readers(arg :: AbstractString, [ type = ArgRead ]) do arg::Function
    ## 预测试设置 ##
    @arg_test arg begin
        arg :: ArgRead
        ## 使用 `arg` 进行测试 ##
    end
    ## 后测试清理 ##
end
```

`arg_readers` 函数接受一个要读取的路径和一个单参数的 do 块，该块对于 `arg_read` 可以处理的每种测试读取器类型被调用一次。如果提供了可选的 `type` 参数，则仅对生成该类型参数的读取器调用 do 块。

传递给 do 块的 `arg` 不是参数值本身，因为某些测试参数类型需要为每个测试用例进行初始化和最终化。考虑一个打开的文件句柄参数：一旦你在一个测试中使用了它，就不能再使用它；你需要关闭它并在下一个测试中重新打开文件。这个函数 `arg` 可以使用 `@arg_test arg begin ... end` 转换为 `ArgRead` 实例。
