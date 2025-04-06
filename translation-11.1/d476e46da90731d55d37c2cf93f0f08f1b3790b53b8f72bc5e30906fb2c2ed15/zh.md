```
Base.runtests(tests=["all"]; ncores=ceil(Int, Sys.CPU_THREADS / 2),
              exit_on_error=false, revise=false, [seed])
```

运行列在 `tests` 中的 Julia 单元测试，`tests` 可以是一个字符串或字符串数组，使用 `ncores` 个处理器。如果 `exit_on_error` 为 `false`，当一个测试失败时，其他文件中的所有剩余测试仍然会被运行；否则，当 `exit_on_error == true` 时，它们会被丢弃。如果 `revise` 为 `true`，则在运行测试之前使用 `Revise` 包加载对 `Base` 或标准库的任何修改。如果通过关键字参数提供了种子，则在运行测试的上下文中用于初始化全局随机数生成器；否则，种子将随机选择。
