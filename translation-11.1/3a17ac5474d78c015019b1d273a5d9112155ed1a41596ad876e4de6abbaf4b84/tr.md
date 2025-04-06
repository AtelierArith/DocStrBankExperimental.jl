```
Simetrik(A::AbstractMatrix, uplo::Symbol=:U)
```

Matris `A`nın üst (eğer `uplo = :U`) veya alt (eğer `uplo = :L`) üçgeninin bir `Simetrik` görünümünü oluşturur.

`Simetrik` görünümler, esas olarak gerçek simetrik matrisler için yararlıdır; bu matrisler için özel algoritmalar (örneğin, özdeğer problemleri için) `Simetrik` türleri için etkinleştirilmiştir. Daha genel olarak, karmaşık matrisler için de yararlı olan `A == A'` koşulunu sağlayan Hermit matrisleri için [`Hermitian(A)`](@ref) kısmına da bakabilirsiniz. (Karmaşık `Simetrik` matrisler desteklenmektedir ancak çok az veya hiç özel algoritma yoktur.)

Gerçek bir matrisin simetrik kısmını veya daha genel olarak bir gerçek veya karmaşık matris `A`nın Hermit kısmını `(A + A') / 2` hesaplamak için [`hermitianpart`](@ref) fonksiyonunu kullanın.

# Örnekler

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> Supper = Simetrik(A)
3×3 Simetrik{Int64, Matrix{Int64}}:
 1  2  3
 2  5  6
 3  6  9

julia> Slower = Simetrik(A, :L)
3×3 Simetrik{Int64, Matrix{Int64}}:
 1  4  7
 4  5  8
 7  8  9

julia> hermitianpart(A)
3×3 Hermitian{Float64, Matrix{Float64}}:
 1.0  3.0  5.0
 3.0  5.0  7.0
 5.0  7.0  9.0
```

`Supper`'ın `Slower` ile eşit olmayacağını unutmayın, eğer `A` kendisi simetrik değilse (örneğin, `A == transpose(A)` ise).
