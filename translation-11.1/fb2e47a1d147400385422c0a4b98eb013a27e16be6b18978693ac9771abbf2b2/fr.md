```
@invoke f(arg::T, ...; kwargs...)
```

Fournit un moyen pratique d'appeler [`invoke`](@ref) en développant `@invoke f(arg1::T1, arg2::T2; kwargs...)` en `invoke(f, Tuple{T1,T2}, arg1, arg2; kwargs...)`. Lorsqu'une annotation de type d'argument est omise, elle est remplacée par `Core.Typeof` de cet argument. Pour invoquer une méthode où un argument n'est pas typé ou est explicitement typé comme `Any`, annotez l'argument avec `::Any`.

Il prend également en charge la syntaxe suivante :

  * `@invoke (x::X).f` se développe en `invoke(getproperty, Tuple{X,Symbol}, x, :f)`
  * `@invoke (x::X).f = v::V` se développe en `invoke(setproperty!, Tuple{X,Symbol,V}, x, :f, v)`
  * `@invoke (xs::Xs)[i::I]` se développe en `invoke(getindex, Tuple{Xs,I}, xs, i)`
  * `@invoke (xs::Xs)[i::I] = v::V` se développe en `invoke(setindex!, Tuple{Xs,V,I}, xs, v, i)`

# Exemples

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
    Ce macro nécessite Julia 1.7 ou une version ultérieure.


!!! compat "Julia 1.9"
    Ce macro est exporté à partir de Julia 1.9.


!!! compat "Julia 1.10"
    La syntaxe supplémentaire est prise en charge à partir de Julia 1.10.

