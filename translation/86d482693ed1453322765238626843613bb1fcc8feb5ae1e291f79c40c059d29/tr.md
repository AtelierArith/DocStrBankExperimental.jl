```
Hermitian(A::AbstractMatrix, uplo::Symbol=:U)
```

`A` matrisinin üst (eğer `uplo = :U`) veya alt (eğer `uplo = :L`) üçgeninin bir `Hermitian` görünümünü oluşturur.

`A`'nın Hermitian kısmını hesaplamak için [`hermitianpart`](@ref) fonksiyonunu kullanın.

# Örnekler

```jldoctest
julia> A = [1 2+2im 3-3im; 4 5 6-6im; 7 8+8im 9]
3×3 Matrix{Complex{Int64}}:
 1+0im  2+2im  3-3im
 4+0im  5+0im  6-6im
 7+0im  8+8im  9+0im

julia> Hupper = Hermitian(A)
3×3 Hermitian{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  2+2im  3-3im
 2-2im  5+0im  6-6im
 3+3im  6+6im  9+0im

julia> Hlower = Hermitian(A, :L)
3×3 Hermitian{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  4+0im  7+0im
 4+0im  5+0im  8-8im
 7+0im  8+8im  9+0im

julia> hermitianpart(A)
3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 1.0+0.0im  3.0+1.0im  5.0-1.5im
 3.0-1.0im  5.0+0.0im  7.0-7.0im
 5.0+1.5im  7.0+7.0im  9.0+0.0im
```

`Hupper`'ın `Hlower` ile eşit olmayacağını unutmayın, eğer `A` kendisi Hermitian değilse (örneğin, eğer `A == adjoint(A)` ise).

Diyagonalın tüm gerçek olmayan kısımları göz ardı edilecektir.

```julia
Hermitian(fill(complex(1,1), 1, 1)) == fill(1, 1, 1)
```
