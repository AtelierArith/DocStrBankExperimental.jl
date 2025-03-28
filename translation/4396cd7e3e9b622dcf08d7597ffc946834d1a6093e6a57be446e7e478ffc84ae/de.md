```
Base.@nospecializeinfer function f(args...)
    @nospecialize ...
    ...
end
Base.@nospecializeinfer f(@nospecialize args...) = ...
```

Weist dem Compiler an, `f` unter Verwendung der deklarierten Typen der `@nospecialize`d-Argumente zu inferieren. Dies kann verwendet werden, um die Anzahl der vom Compiler generierten Spezialisierungen während der Inferenz zu begrenzen.

# Beispiele

```julia
julia> f(A::AbstractArray) = g(A)
f (generische Funktion mit 1 Methode)

julia> @noinline Base.@nospecializeinfer g(@nospecialize(A::AbstractArray)) = A[1]
g (generische Funktion mit 1 Methode)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Any
└──      return %1
) => Any
```

In diesem Beispiel wird `f` für jeden spezifischen Typ von `A` inferiert, aber `g` wird nur einmal mit dem deklarierten Argumenttyp `A::AbstractArray` inferiert, was bedeutet, dass der Compiler wahrscheinlich die übermäßige Inferenzzeit dafür nicht sehen wird, während er den konkreten Rückgabetyp davon nicht inferieren kann. Ohne das `@nospecializeinfer` würde `f([1.0])` den Rückgabetyp von `g` als `Float64` inferieren, was darauf hinweist, dass die Inferenz für `g(::Vector{Float64})` lief, trotz des Verbots der spezialisierten Codegenerierung.

!!! compat "Julia 1.10"
    Die Verwendung von `Base.@nospecializeinfer` erfordert die Julia-Version 1.10.

