```
@invoke f(arg::T, ...; kwargs...)
```

提供了一种方便的方式来调用 [`invoke`](@ref)，通过将 `@invoke f(arg1::T1, arg2::T2; kwargs...)` 扩展为 `invoke(f, Tuple{T1,T2}, arg1, arg2; kwargs...)`。当参数的类型注释被省略时，它会被替换为 `Core.Typeof` 该参数。要调用一个参数未类型化或显式类型为 `Any` 的方法，请使用 `::Any` 注释该参数。

它还支持以下语法：

  * `@invoke (x::X).f` 扩展为 `invoke(getproperty, Tuple{X,Symbol}, x, :f)`
  * `@invoke (x::X).f = v::V` 扩展为 `invoke(setproperty!, Tuple{X,Symbol,V}, x, :f, v)`
  * `@invoke (xs::Xs)[i::I]` 扩展为 `invoke(getindex, Tuple{Xs,I}, xs, i)`
  * `@invoke (xs::Xs)[i::I] = v::V` 扩展为 `invoke(setindex!, Tuple{Xs,V,I}, xs, v, i)`

# 示例

```jldoctest
julia> @macroexpand @invoke f(x::T, y)
:(Core.invoke(f, Tuple{T, Core.Typeof(y)}, x, y))

julia> @invoke 420::Integer % Unsigned
0x00000000000001a4

julia> @macroexpand @invoke (x::X).f
:(Core.invoke(Base.getproperty, Tuple{X, Core.Typeof(:f)}, x, :f))

julia> @macroexpand @invoke (x::X).f = v::V
:(Core.invoke(Base.setproperty!, Tuple{X, Core.Typeof(:f), V}, x, :f, v))

julia> @macroexpand @invoke (xs::Xs)[i::I]
:(Core.invoke(Base.getindex, Tuple{Xs, I}, xs, i))

julia> @macroexpand @invoke (xs::Xs)[i::I] = v::V
:(Core.invoke(Base.setindex!, Tuple{Xs, V, I}, xs, v, i))
```

!!! compat "Julia 1.7"
    此宏需要 Julia 1.7 或更高版本。


!!! compat "Julia 1.9"
    此宏自 Julia 1.9 起被导出。


!!! compat "Julia 1.10"
    从 Julia 1.10 开始支持额外的语法。

