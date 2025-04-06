```
@invoke f(arg::T, ...; kwargs...)
```

Bietet eine bequeme Möglichkeit, [`invoke`](@ref) aufzurufen, indem `@invoke f(arg1::T1, arg2::T2; kwargs...)` auf `invoke(f, Tuple{T1,T2}, arg1, arg2; kwargs...)` erweitert wird. Wenn die Typannotation eines Arguments weggelassen wird, wird sie durch `Core.Typeof` dieses Arguments ersetzt. Um eine Methode aufzurufen, bei der ein Argument untypisiert oder explizit als `Any` typisiert ist, annotiere das Argument mit `::Any`.

Es unterstützt auch die folgende Syntax:

  * `@invoke (x::X).f` wird zu `invoke(getproperty, Tuple{X,Symbol}, x, :f)` erweitert
  * `@invoke (x::X).f = v::V` wird zu `invoke(setproperty!, Tuple{X,Symbol,V}, x, :f, v)` erweitert
  * `@invoke (xs::Xs)[i::I]` wird zu `invoke(getindex, Tuple{Xs,I}, xs, i)` erweitert
  * `@invoke (xs::Xs)[i::I] = v::V` wird zu `invoke(setindex!, Tuple{Xs,V,I}, xs, v, i)` erweitert

# Beispiele

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
    Dieses Makro erfordert Julia 1.7 oder höher.


!!! compat "Julia 1.9"
    Dieses Makro wird seit Julia 1.9 exportiert.


!!! compat "Julia 1.10"
    Die zusätzliche Syntax wird seit Julia 1.10 unterstützt.

