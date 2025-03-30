```
fetch(t::Task)
```

等待一个 [`Task`](@ref) 完成，然后返回其结果值。如果任务因异常而失败，将抛出一个 [`TaskFailedException`](@ref)（它包装了失败的任务）。
