```
current_exceptions(task::Task=current_task(); [backtrace::Bool=true])
```

获取当前正在处理的异常堆栈。对于嵌套的捕获块，可能会有多个当前异常，在这种情况下，最近抛出的异常在堆栈的最后。堆栈作为 `ExceptionStack` 返回，它是命名元组 `(exception,backtrace)` 的 AbstractVector。如果 `backtrace` 为 false，则每对中的回溯将被设置为 `nothing`。

显式传递 `task` 将返回任意任务上的当前异常堆栈。这对于检查由于未捕获异常而失败的任务非常有用。

!!! compat "Julia 1.7"
    这个函数在 Julia 1.1–1.6 中以实验性名称 `catch_stack()` 存在，并且返回类型是一个普通的元组向量。

