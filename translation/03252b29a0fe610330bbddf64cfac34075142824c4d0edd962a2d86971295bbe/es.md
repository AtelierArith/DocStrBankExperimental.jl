```
PermutedDimsArray(A, perm) -> B
```

Dada una `AbstractArray` `A`, crea una vista `B` de tal manera que las dimensiones parezcan estar permutadas. Similar a `permutedims`, excepto que no se realiza copia ( `B` comparte almacenamiento con `A`).

Véase también [`permutedims`](@ref), [`invperm`](@ref).

# Ejemplos

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
