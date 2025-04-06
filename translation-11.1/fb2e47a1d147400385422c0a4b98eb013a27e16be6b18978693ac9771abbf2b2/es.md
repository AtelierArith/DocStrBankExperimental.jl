```
@invoke f(arg::T, ...; kwargs...)
```

Proporciona una forma conveniente de llamar a [`invoke`](@ref) al expandir `@invoke f(arg1::T1, arg2::T2; kwargs...)` a `invoke(f, Tuple{T1,T2}, arg1, arg2; kwargs...)`. Cuando se omite la anotación de tipo de un argumento, se reemplaza por `Core.Typeof` de ese argumento. Para invocar un método donde un argumento no tiene tipo o está explícitamente tipado como `Any`, anota el argumento con `::Any`.

También admite la siguiente sintaxis:

  * `@invoke (x::X).f` se expande a `invoke(getproperty, Tuple{X,Symbol}, x, :f)`
  * `@invoke (x::X).f = v::V` se expande a `invoke(setproperty!, Tuple{X,Symbol,V}, x, :f, v)`
  * `@invoke (xs::Xs)[i::I]` se expande a `invoke(getindex, Tuple{Xs,I}, xs, i)`
  * `@invoke (xs::Xs)[i::I] = v::V` se expande a `invoke(setindex!, Tuple{Xs,V,I}, xs, v, i)`

# Ejemplos

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
    Esta macro requiere Julia 1.7 o posterior.


!!! compat "Julia 1.9"
    Esta macro se exporta a partir de Julia 1.9.


!!! compat "Julia 1.10"
    La sintaxis adicional es compatible a partir de Julia 1.10.

