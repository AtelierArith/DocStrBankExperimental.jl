```
A'
adjoint(A)
```

Tembel adjoint (karmaşık transpozisyon). `adjoint`'in elemanlara özyinelemeli olarak uygulandığını unutmayın.

Sayı türleri için `adjoint`, karmaşık eşleniği döndürür ve bu nedenle gerçek sayılar için kimlik fonksiyonu ile eşdeğerdir.

Bu işlem, lineer cebir kullanımı için tasarlanmıştır - genel veri manipülasyonu için [`permutedims`](@ref Base.permutedims) bakın.

# Örnekler

```jldoctest
julia> A = [3+2im 9+2im; 0  0]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 0+0im  0+0im

julia> B = A' # eşdeğer olarak adjoint(A)
2×2 adjoint(::Matrix{Complex{Int64}}) with eltype Complex{Int64}:
 3-2im  0+0im
 9-2im  0+0im

julia> B isa Adjoint
true

julia> adjoint(B) === A # bir adjoint'in adjoint'i üst öğeyi açar
true

julia> Adjoint(B) # ancak, yapıcı her zaman argümanını sarar
2×2 adjoint(adjoint(::Matrix{Complex{Int64}})) with eltype Complex{Int64}:
 3+2im  9+2im
 0+0im  0+0im

julia> B[1,2] = 4 + 5im; # B'yi değiştirmek A'yı otomatik olarak değiştirir

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 4-5im  0+0im
```

Gerçek matrisler için `adjoint` işlemi, bir `transpose` ile eşdeğerdir.

```jldoctest
julia> A = reshape([x for x in 1:4], 2, 2)
2×2 Matrix{Int64}:
 1  3
 2  4

julia> A'
2×2 adjoint(::Matrix{Int64}) with eltype Int64:
 1  2
 3  4

julia> adjoint(A) == transpose(A)
true
```

Bir `AbstractVector`'ın adjoint'i bir satır vektörüdür:

```jldoctest
julia> x = [3, 4im]
2-element Vector{Complex{Int64}}:
 3 + 0im
 0 + 4im

julia> x'
1×2 adjoint(::Vector{Complex{Int64}}) with eltype Complex{Int64}:
 3+0im  0-4im

julia> x'x # nokta çarpımını hesapla, eşdeğer olarak x' * x
25 + 0im
```

Matrislerin matrisleri için, bireysel bloklar özyinelemeli olarak işlenir:

```jldoctest
julia> A = reshape([x + im*x for x in 1:4], 2, 2)
2×2 Matrix{Complex{Int64}}:
 1+1im  3+3im
 2+2im  4+4im

julia> C = reshape([A, 2A, 3A, 4A], 2, 2)
2×2 Matrix{Matrix{Complex{Int64}}}:
 [1+1im 3+3im; 2+2im 4+4im]  [3+3im 9+9im; 6+6im 12+12im]
 [2+2im 6+6im; 4+4im 8+8im]  [4+4im 12+12im; 8+8im 16+16im]

julia> C'
2×2 adjoint(::Matrix{Matrix{Complex{Int64}}}) with eltype Adjoint{Complex{Int64}, Matrix{Complex{Int64}}}:
 [1-1im 2-2im; 3-3im 4-4im]    [2-2im 4-4im; 6-6im 8-8im]
 [3-3im 6-6im; 9-9im 12-12im]  [4-4im 8-8im; 12-12im 16-16im]
```
