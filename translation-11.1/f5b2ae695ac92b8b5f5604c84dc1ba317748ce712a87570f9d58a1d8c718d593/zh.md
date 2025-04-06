```
disable_sigint(f::Function)
```

在当前任务中执行函数时禁用 Ctrl-C 处理程序，以便调用可能会调用不安全的 julia 代码的外部代码。旨在使用 `do` 块语法调用，如下所示：

```
disable_sigint() do
    # 不安全的中断代码
    ...
end
```

在工作线程上不需要这样做（`Threads.threadid() != 1`），因为 `InterruptException` 只会发送到主线程。未调用 julia 代码或 julia 运行时的外部函数在执行期间会自动禁用 sigint。
