```
@inferred [允许类型] f(x)
```

测试调用表达式 `f(x)` 是否返回与编译器推断的相同类型的值。这对于检查类型稳定性非常有用。

`f(x)` 可以是任何调用表达式。如果类型匹配，则返回 `f(x)` 的结果；如果发现不同类型，则返回 `Error` `Result`。

可选地，`允许类型` 放宽了测试，当 `f(x)` 的类型与推断类型在 `允许类型` 的模下匹配，或者返回类型是 `允许类型` 的子类型时，测试将通过。这在测试返回小联合类型的函数的类型稳定性时非常有用，例如 `Union{Nothing, T}` 或 `Union{Missing, T}`。

```jldoctest; setup = :(using InteractiveUtils; using Base: >), filter = r"begin\n(.|\n)*end"
julia> f(a) = a > 1 ? 1 : 1.0
f (generic function with 1 method)

julia> typeof(f(2))
Int64

julia> @code_warntype f(2)
MethodInstance for f(::Int64)
  from f(a) @ Main none:1
Arguments
  #self#::Core.Const(f)
  a::Int64
Body::UNION{FLOAT64, INT64}
1 ─ %1 = (a > 1)::Bool
└──      goto #3 if not %1
2 ─      return 1
3 ─      return 1.0

julia> @inferred f(2)
错误: 返回类型 Int64 与推断返回类型 Union{Float64, Int64} 不匹配
[...]

julia> @inferred max(1, 2)
2

julia> g(a) = a < 10 ? missing : 1.0
g (generic function with 1 method)

julia> @inferred g(20)
错误: 返回类型 Float64 与推断返回类型 Union{Missing, Float64} 不匹配
[...]

julia> @inferred Missing g(20)
1.0

julia> h(a) = a < 10 ? missing : f(a)
h (generic function with 1 method)

julia> @inferred Missing h(20)
错误: 返回类型 Int64 与推断返回类型 Union{Missing, Float64, Int64} 不匹配
[...]
```
