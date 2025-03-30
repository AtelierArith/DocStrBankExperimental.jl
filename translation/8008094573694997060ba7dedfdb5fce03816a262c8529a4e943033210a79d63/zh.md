```
@deprecate old new [export_old=true]
```

弃用方法 `old` 并指定替代调用 `new`，同时定义一个具有指定签名的新方法 `old`。

要防止 `old` 被导出，将 `export_old` 设置为 `false`。

另见 [`Base.depwarn()`](@ref)。

!!! compat "Julia 1.5"
    从 Julia 1.5 开始，当 `julia` 在未设置 `--depwarn=yes` 标志的情况下运行时，通过 `@deprecate` 定义的函数不会打印警告，因为 `--depwarn` 选项的默认值为 `no`。 警告是通过 `Pkg.test()` 运行的测试打印的。


# 示例

```jldoctest
julia> @deprecate old(x) new(x)
old (generic function with 1 method)

julia> @deprecate old(x) new(x) false
old (generic function with 1 method)
```

没有显式类型注释的 `@deprecate` 调用将定义接受任意数量位置参数和关键字参数类型为 `Any` 的弃用方法。

!!! compat "Julia 1.9"
    从 Julia 1.9 开始，当没有显式类型注释时，关键字参数会被转发。对于旧版本，您可以通过 `@deprecate old(args...; kwargs...) new(args...; kwargs...)` 手动转发位置参数和关键字参数。


要将弃用限制为特定签名，请注释 `old` 的参数。例如，

```jldoctest; filter = r"@ .*"a
julia> new(x::Int) = x;

julia> new(x::Float64) = 2x;

julia> @deprecate old(x::Int) new(x);

julia> methods(old)
# 1 method for generic function "old" from Main:
 [1] old(x::Int64)
     @ deprecated.jl:94
```

将定义并弃用一个方法 `old(x::Int)`，该方法与 `new(x::Int)` 相对应，但不会定义或弃用方法 `old(x::Float64)`。
