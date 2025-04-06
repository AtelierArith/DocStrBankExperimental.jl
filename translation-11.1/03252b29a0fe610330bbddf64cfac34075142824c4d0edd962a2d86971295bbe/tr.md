```
PermutedDimsArray(A, perm) -> B
```

Bir AbstractArray `A` verildiğinde, boyutların permütasyonlu göründüğü bir görünüm `B` oluşturun. `permutedims` ile benzer, ancak kopyalama gerçekleşmez (`B`, `A` ile depolama paylaşır).

Ayrıca bkz. [`permutedims`](@ref), [`invperm`](@ref).

# Örnekler

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
