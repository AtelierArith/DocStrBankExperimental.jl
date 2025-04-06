```
@invokelatest f(args...; kwargs...)
```

Bietet eine bequeme Möglichkeit, [`invokelatest`](@ref) aufzurufen. `@invokelatest f(args...; kwargs...)` wird einfach in `Base.invokelatest(f, args...; kwargs...)` umgewandelt.

Es unterstützt auch die folgende Syntax:

  * `@invokelatest x.f` wird zu `Base.invokelatest(getproperty, x, :f)` umgewandelt
  * `@invokelatest x.f = v` wird zu `Base.invokelatest(setproperty!, x, :f, v)` umgewandelt
  * `@invokelatest xs[i]` wird zu `Base.invokelatest(getindex, xs, i)` umgewandelt
  * `@invokelatest xs[i] = v` wird zu `Base.invokelatest(setindex!, xs, v, i)` umgewandelt

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
    Dieses Makro erfordert Julia 1.7 oder höher.


!!! compat "Julia 1.9"
    Vor Julia 1.9 wurde dieses Makro nicht exportiert und wurde als `Base.@invokelatest` aufgerufen.


!!! compat "Julia 1.10"
    Die zusätzliche Syntax `x.f` und `xs[i]` erfordert Julia 1.10.

