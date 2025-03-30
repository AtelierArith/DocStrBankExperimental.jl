```
@invokelatest f(args...; kwargs...)
```

提供了一种方便的方式来调用 [`invokelatest`](@ref)。 `@invokelatest f(args...; kwargs...)` 将简单地扩展为 `Base.invokelatest(f, args...; kwargs...)`。

它还支持以下语法：

  * `@invokelatest x.f` 扩展为 `Base.invokelatest(getproperty, x, :f)`
  * `@invokelatest x.f = v` 扩展为 `Base.invokelatest(setproperty!, x, :f, v)`
  * `@invokelatest xs[i]` 扩展为 `Base.invokelatest(getindex, xs, i)`
  * `@invokelatest xs[i] = v` 扩展为 `Base.invokelatest(setindex!, xs, v, i)`

```jldoctest
julia> @macroexpand @invokelatest f(x; kw=kwv)
:(Base.invokelatest(f, x; kw = kwv))

julia> @macroexpand @invokelatest x.f
:(Base.invokelatest(Base.getproperty, x, :f))

julia> @macroexpand @invokelatest x.f = v
:(Base.invokelatest(Base.setproperty!, x, :f, v))

julia> @macroexpand @invokelatest xs[i]
:(Base.invokelatest(Base.getindex, xs, i))

julia> @macroexpand @invokelatest xs[i] = v
:(Base.invokelatest(Base.setindex!, xs, v, i))
```

!!! compat "Julia 1.7"
    此宏需要 Julia 1.7 或更高版本。


!!! compat "Julia 1.9"
    在 Julia 1.9 之前，此宏未被导出，并被称为 `Base.@invokelatest`。


!!! compat "Julia 1.10"
    额外的 `x.f` 和 `xs[i]` 语法需要 Julia 1.10。

