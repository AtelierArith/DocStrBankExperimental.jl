```
Threads.threadid() -> Int
```

获取当前执行线程的 ID 号。主线程的 ID 为 `1`。

# 示例

```julia-repl
julia> Threads.threadid()
1

julia> Threads.@threads for i in 1:4
          println(Threads.threadid())
       end
4
2
5
4
```

!!! 注意     任务运行的线程可能会在任务让出时发生变化，这被称为 [`Task Migration`](@ref man-task-migration)。因此，在大多数情况下，使用 `threadid()` 来索引，例如，缓冲区或状态对象的向量是不安全的。
