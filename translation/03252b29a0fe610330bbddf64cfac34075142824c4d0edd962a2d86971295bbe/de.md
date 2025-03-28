```
PermutedDimsArray(A, perm) -> B
```

Gegeben ein AbstractArray `A`, erstellen Sie eine Ansicht `B`, sodass die Dimensionen permutiert erscheinen. Ähnlich wie `permutedims`, jedoch ohne Kopieren ( `B` teilt den Speicher mit `A`).

Siehe auch [`permutedims`](@ref), [`invperm`](@ref).

# Beispiele

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
