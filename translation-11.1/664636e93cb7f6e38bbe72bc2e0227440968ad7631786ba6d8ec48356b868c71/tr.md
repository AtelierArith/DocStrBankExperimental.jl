```
transpose(A)
```

Tembel transpoze. Döndürülen nesnenin değiştirilmesi, `A`'yı uygun şekilde değiştirmelidir. Genellikle, ama her zaman değil, `Transpose(A)` verir; burada `Transpose`, tembel bir transpoze sarmalayıcıdır. Bu işlemin özyinelemeli olduğunu unutmayın.

Bu işlem, lineer cebir kullanımı için tasarlanmıştır - genel veri manipülasyonu için [`permutedims`](@ref Base.permutedims) bakın, bu özyinelemeli değildir.

# Örnekler

```jldoctest
julia> A = [3 2; 0 0]
2×2 Matrix{Int64}:
 3  2
 0  0

julia> B = transpose(A)
2×2 transpose(::Matrix{Int64}) with eltype Int64:
 3  0
 2  0

julia> B isa Transpose
true

julia> transpose(B) === A # bir transpozenin transpozu üst nesneyi açar
true

julia> Transpose(B) # ancak, yapıcı her zaman argümanını sarar
2×2 transpose(transpose(::Matrix{Int64})) with eltype Int64:
 3  2
 0  0

julia> B[1,2] = 4; # B'yi değiştirmek A'yı otomatik olarak değiştirecektir

julia> A
2×2 Matrix{Int64}:
 3  2
 4  0
```

Karmaşık matrisler için `adjoint` işlemi, bir konjugat-transpoze ile eşdeğerdir.

```jldoctest
julia> A = reshape([Complex(x, x) for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> adjoint(A) == conj(transpose(A))
true
```

Bir `AbstractVector`'ın `transpose`'u bir satır vektörüdür:

```jldoctest
julia> v = [1,2,3]
3-element Vector{Int64}:
 1
 2
 3

julia> transpose(v) # bir satır vektörü döndürür
1×3 transpose(::Vector{Int64}) with eltype Int64:
 1  2  3

julia> transpose(v) * v # nokta çarpımını hesapla
14
```

Matrislerden oluşan bir matris için, bireysel bloklar özyinelemeli olarak işlenir:

```jldoctest
julia> C = [1 3; 2 4]
2×2 Matrix{Int64}:
 1  3
 2  4

julia> D = reshape([C, 2C, 3C, 4C], 2, 2) # bir blok matris oluştur
2×2 Matrix{Matrix{Int64}}:
 [1 3; 2 4]  [3 9; 6 12]
 [2 6; 4 8]  [4 12; 8 16]

julia> transpose(D) # bloklar özyinelemeli olarak transpoze edilir
2×2 transpose(::Matrix{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 2; 3 4]   [2 4; 6 8]
 [3 6; 9 12]  [4 8; 12 16]
```
