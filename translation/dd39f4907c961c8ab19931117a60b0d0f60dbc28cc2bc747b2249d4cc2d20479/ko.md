```
@invokelatest f(args...; kwargs...)
```

[`invokelatest`](@ref)를 호출하는 편리한 방법을 제공합니다. `@invokelatest f(args...; kwargs...)`는 단순히 `Base.invokelatest(f, args...; kwargs...)`로 확장됩니다.

다음 구문도 지원합니다:

  * `@invokelatest x.f`는 `Base.invokelatest(getproperty, x, :f)`로 확장됩니다.
  * `@invokelatest x.f = v`는 `Base.invokelatest(setproperty!, x, :f, v)`로 확장됩니다.
  * `@invokelatest xs[i]`는 `Base.invokelatest(getindex, xs, i)`로 확장됩니다.
  * `@invokelatest xs[i] = v`는 `Base.invokelatest(setindex!, xs, v, i)`로 확장됩니다.

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
    이 매크로는 Julia 1.7 이상이 필요합니다.


!!! compat "Julia 1.9"
    Julia 1.9 이전에는 이 매크로가 내보내지지 않았으며, `Base.@invokelatest`로 호출되었습니다.


!!! compat "Julia 1.10"
    추가적인 `x.f` 및 `xs[i]` 구문은 Julia 1.10이 필요합니다.

