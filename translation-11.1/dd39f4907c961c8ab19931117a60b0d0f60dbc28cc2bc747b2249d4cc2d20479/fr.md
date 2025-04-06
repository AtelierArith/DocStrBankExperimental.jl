```
@invokelatest f(args...; kwargs...)
```

Fournit un moyen pratique d'appeler [`invokelatest`](@ref). `@invokelatest f(args...; kwargs...)` sera simplement développé en `Base.invokelatest(f, args...; kwargs...)`.

Il prend également en charge la syntaxe suivante :

  * `@invokelatest x.f` se développe en `Base.invokelatest(getproperty, x, :f)`
  * `@invokelatest x.f = v` se développe en `Base.invokelatest(setproperty!, x, :f, v)`
  * `@invokelatest xs[i]` se développe en `Base.invokelatest(getindex, xs, i)`
  * `@invokelatest xs[i] = v` se développe en `Base.invokelatest(setindex!, xs, v, i)`

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
    Cette macro nécessite Julia 1.7 ou une version ultérieure.


!!! compat "Julia 1.9"
    Avant Julia 1.9, cette macro n'était pas exportée et était appelée comme `Base.@invokelatest`.


!!! compat "Julia 1.10"
    La syntaxe supplémentaire `x.f` et `xs[i]` nécessite Julia 1.10.

