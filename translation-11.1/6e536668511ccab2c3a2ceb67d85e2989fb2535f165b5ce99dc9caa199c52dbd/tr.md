```
diagind(M::AbstractMatrix, k::Integer = 0, indstyle::IndexStyle = IndexLinear())
diagind(M::AbstractMatrix, indstyle::IndexStyle = IndexLinear())
```

`M` matrisinin `k`'nci diyagonalinin indekslerini veren bir `AbstractRange`. İsteğe bağlı olarak, döndürülen aralığın türünü belirleyen bir indeks stili belirtilebilir. Eğer `indstyle isa IndexLinear` (varsayılan), bu bir `AbstractRange{Integer}` döndürür. Öte yandan, eğer `indstyle isa IndexCartesian` ise, bu bir `AbstractRange{CartesianIndex{2}}` döndürür.

Eğer `k` sağlanmazsa, `0` (ana diyagonal ile ilişkili) olduğu varsayılır.

Ayrıca bakınız: [`diag`](@ref), [`diagm`](@ref), [`Diagonal`](@ref).

# Örnekler

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> diagind(A, -1)
2:4:6

julia> diagind(A, IndexCartesian())
StepRangeLen(CartesianIndex(1, 1), CartesianIndex(1, 1), 3)
```

!!! compat "Julia 1.11"
    Bir `IndexStyle` belirtmek en az Julia 1.11 gerektirir.

