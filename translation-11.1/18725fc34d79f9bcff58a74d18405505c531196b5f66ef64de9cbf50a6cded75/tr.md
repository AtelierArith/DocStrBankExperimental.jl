```
view(A, inds...)
```

[`getindex`](@ref) ile benzer, ancak belirtilen indeks veya indeksler `inds` üzerinde ana dizi `A`'ya tembel bir şekilde referans veren (veya etkili bir şekilde bir *görünüm* olan) hafif bir dizi döndürür; bu, elemanları hevesle çıkarmak veya kopyalanmış bir alt küme oluşturmak yerine. Döndürülen değere (`SubArray`(@ref) sıklıkla) [`getindex`](@ref) veya [`setindex!`](@ref) çağrıldığında, ana diziye erişmek veya onu değiştirmek için indeksler anında hesaplanır. `view` çağrıldıktan sonra ana dizinin şekli değiştirilirse davranış belirsizdir çünkü ana dizi için bir sınır kontrolü yoktur; örneğin, bu bir segmentasyon hatasına neden olabilir.

Bazı değişmez ana diziler (aralıklar gibi) bazı durumlarda `SubArray` döndürmek yerine yeni bir dizi yeniden hesaplamayı tercih edebilir, eğer bu verimli ve uyumlu bir anlam sağlıyorsa.

!!! compat "Julia 1.6"
    Julia 1.6 veya daha yeni sürümlerde, `view` bir `AbstractString` üzerinde çağrılabilir ve bir `SubString` döndürür.


# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> b = view(A, :, 1)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 1
 3

julia> fill!(b, 0)
2-element view(::Matrix{Int64}, :, 1) with eltype Int64:
 0
 0

julia> A # Not A değişti, b'yi değiştirdiğimiz halde
2×2 Matrix{Int64}:
 0  2
 0  4

julia> view(2:5, 2:3) # tür değişmez olduğu için bir aralık döndürür
3:4
```
