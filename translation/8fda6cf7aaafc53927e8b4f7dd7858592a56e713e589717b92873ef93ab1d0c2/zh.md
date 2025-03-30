```
@time expr
@time "描述" expr
```

一个宏，用于执行一个表达式，打印执行所花费的时间、分配的数量以及执行导致的总字节数的分配，然后返回表达式的值。任何花费在垃圾收集（gc）、编译新代码或重新编译失效代码上的时间以百分比形式显示。任何需要等待的 [`ReentrantLock`](@ref) 的锁冲突以计数形式显示。

可选地提供一个描述字符串，在时间报告之前打印。

在某些情况下，系统会在 `@time` 表达式内部查看并在顶层表达式执行开始之前编译一些被调用的代码。当发生这种情况时，一些编译时间将不会被计算。要包括这段时间，可以运行 `@time @eval ...`。

另请参见 [`@showtime`](@ref)、[`@timev`](@ref)、[`@timed`](@ref)、[`@elapsed`](@ref)、[`@allocated`](@ref) 和 [`@allocations`](@ref)。

!!! note
    对于更严肃的基准测试，考虑使用 BenchmarkTools.jl 包中的 `@btime` 宏，该宏在多次评估函数以减少噪声等方面表现出色。


!!! compat "Julia 1.8"
    添加描述的选项是在 Julia 1.8 中引入的。

    编译时间与重新编译时间分开显示是在 Julia 1.8 中引入的。


!!! compat "Julia 1.11"
    在 Julia 1.11 中添加了任何锁冲突的报告。


```julia-repl
julia> x = rand(10,10);

julia> @time x * x;
  0.606588 秒 (2.19 M 分配: 116.555 MiB, 3.75% gc 时间, 99.94% 编译时间)

julia> @time x * x;
  0.000009 秒 (1 分配: 896 字节)

julia> @time begin
           sleep(0.3)
           1+1
       end
  0.301395 秒 (8 分配: 336 字节)
2

julia> @time "一秒的睡眠" sleep(1)
一秒的睡眠: 1.005750 秒 (5 分配: 144 字节)

julia> for loop in 1:3
            @time loop sleep(1)
        end
1: 1.006760 秒 (5 分配: 144 字节)
2: 1.001263 秒 (5 分配: 144 字节)
3: 1.003676 秒 (5 分配: 144 字节)
```
