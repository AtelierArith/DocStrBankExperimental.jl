```
@invokelatest f(args...; kwargs...)
```

Proporciona una forma conveniente de llamar a [`invokelatest`](@ref). `@invokelatest f(args...; kwargs...)` simplemente se expandirá en `Base.invokelatest(f, args...; kwargs...)`.

También admite la siguiente sintaxis:

  * `@invokelatest x.f` se expande a `Base.invokelatest(getproperty, x, :f)`
  * `@invokelatest x.f = v` se expande a `Base.invokelatest(setproperty!, x, :f, v)`
  * `@invokelatest xs[i]` se expande a `Base.invokelatest(getindex, xs, i)`
  * `@invokelatest xs[i] = v` se expande a `Base.invokelatest(setindex!, xs, v, i)`

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
    Esta macro requiere Julia 1.7 o posterior.


!!! compat "Julia 1.9"
    Antes de Julia 1.9, esta macro no se exportaba y se llamaba como `Base.@invokelatest`.


!!! compat "Julia 1.10"
    La sintaxis adicional `x.f` y `xs[i]` requiere Julia 1.10.

