```
Channel{T=Any}(func::Function, size=0; taskref=nothing, spawn=false, threadpool=nothing)
```

从 `func` 创建一个新任务，将其绑定到类型为 `T` 和大小为 `size` 的新通道，并在一次调用中调度该任务。当任务终止时，通道会自动关闭。

`func` 必须将绑定的通道作为其唯一参数。

如果您需要对创建的任务的引用，请通过关键字参数 `taskref` 传递一个 `Ref{Task}` 对象。

如果 `spawn=true`，为 `func` 创建的 `Task` 可能会在另一个线程上并行调度，相当于通过 [`Threads.@spawn`](@ref) 创建任务。

如果 `spawn=true` 且未设置 `threadpool` 参数，则默认为 `:default`。

如果设置了 `threadpool` 参数（为 `:default` 或 `:interactive`），这意味着 `spawn=true`，并且新的任务被分配到指定的线程池。

返回一个 `Channel`。

# 示例

```jldoctest
julia> chnl = Channel() do ch
           foreach(i -> put!(ch, i), 1:4)
       end;

julia> typeof(chnl)
Channel{Any}

julia> for i in chnl
           @show i
       end;
i = 1
i = 2
i = 3
i = 4
```

引用创建的任务：

```jldoctest
julia> taskref = Ref{Task}();

julia> chnl = Channel(taskref=taskref) do ch
           println(take!(ch))
       end;

julia> istaskdone(taskref[])
false

julia> put!(chnl, "Hello");
Hello

julia> istaskdone(taskref[])
true
```

!!! compat "Julia 1.3"
    `spawn=` 参数是在 Julia 1.3 中添加的。此构造函数是在 Julia 1.3 中添加的。在早期版本的 Julia 中，Channel 使用关键字参数来设置 `size` 和 `T`，但这些构造函数已被弃用。


!!! compat "Julia 1.9"
    `threadpool=` 参数是在 Julia 1.9 中添加的。


```jldoctest
julia> chnl = Channel{Char}(1, spawn=true) do ch
           for c in "hello world"
               put!(ch, c)
           end
       end
Channel{Char}(1) (2 items available)

julia> String(collect(chnl))
"hello world"
```
