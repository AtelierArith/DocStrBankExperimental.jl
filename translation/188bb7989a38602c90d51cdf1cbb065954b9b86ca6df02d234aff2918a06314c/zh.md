```
@timev expr
@timev "description" expr
```

这是 `@time` 宏的详细版本。它首先打印与 `@time` 相同的信息，然后打印任何非零的内存分配计数器，最后返回表达式的值。

可选地提供一个描述字符串，在时间报告之前打印。

!!! compat "Julia 1.8"
    添加描述的选项是在 Julia 1.8 中引入的。


另请参见 [`@time`](@ref)、[`@timed`](@ref)、[`@elapsed`](@ref)、[`@allocated`](@ref) 和 [`@allocations`](@ref)。

```julia-repl
julia> x = rand(10,10);

julia> @timev x * x;
  0.546770 seconds (2.20 M allocations: 116.632 MiB, 4.23% gc time, 99.94% compilation time)
elapsed time (ns): 546769547
gc time (ns):      23115606
bytes allocated:   122297811
pool allocs:       2197930
non-pool GC allocs:1327
malloc() calls:    36
realloc() calls:   5
GC pauses:         3

julia> @timev x * x;
  0.000010 seconds (1 allocation: 896 bytes)
elapsed time (ns): 9848
bytes allocated:   896
pool allocs:       1
```
