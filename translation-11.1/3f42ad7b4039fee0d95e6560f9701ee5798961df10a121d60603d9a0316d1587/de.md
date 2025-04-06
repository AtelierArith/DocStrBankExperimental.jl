```
Array{T}(undef, dims)
Array{T,N}(undef, dims)
```

Konstruiere ein nicht initialisiertes `N`-dimensionales [`Array`](@ref), das Elemente des Typs `T` enthält. `N` kann entweder explizit angegeben werden, wie in `Array{T,N}(undef, dims)`, oder durch die Länge oder Anzahl von `dims` bestimmt werden. `dims` kann ein Tupel oder eine Reihe von ganzzahligen Argumenten sein, die den Längen in jeder Dimension entsprechen. Wenn der Rang `N` explizit angegeben wird, muss er mit der Länge oder Anzahl von `dims` übereinstimmen. Hier ist [`undef`](@ref) der [`UndefInitializer`](@ref).

# Beispiele

```julia-repl
julia> A = Array{Float64, 2}(undef, 2, 3) # N wird explizit angegeben
2×3 Matrix{Float64}:
 6.90198e-310  6.90198e-310  6.90198e-310
 6.90198e-310  6.90198e-310  0.0

julia> B = Array{Float64}(undef, 4) # N wird durch die Eingabe bestimmt
4-element Vector{Float64}:
   2.360075077e-314
 NaN
   2.2671131793e-314
   2.299821756e-314

julia> similar(B, 2, 4, 1) # verwende typeof(B) und die angegebene Größe
2×4×1 Array{Float64, 3}:
[:, :, 1] =
 2.26703e-314  2.26708e-314  0.0           2.80997e-314
 0.0           2.26703e-314  2.26708e-314  0.0
```
