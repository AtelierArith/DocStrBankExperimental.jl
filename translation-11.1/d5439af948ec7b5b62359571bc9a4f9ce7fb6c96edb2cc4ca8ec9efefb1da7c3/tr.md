```
CartesianIndices(sz::Dims) -> R
CartesianIndices((istart:[istep:]istop, jstart:[jstep:]jstop, ...)) -> R
```

Bir bölge `R` tanımlayın, bu bölge çok boyutlu dikdörtgen bir tam sayı indeks aralığını kapsar. Bu genellikle yineleme bağlamında karşılaşılır; burada `for I in R ... end` ifadesi, iç içe döngülere eşdeğer [`CartesianIndex`](@ref) indeksleri `I` döndürecektir.

```
for j = jstart:jstep:jstop
    for i = istart:istep:istop
        ...
    end
end
```

Sonuç olarak, bunlar, rastgele boyutlarda çalışan algoritmalar yazmak için yararlı olabilir.

```
CartesianIndices(A::AbstractArray) -> R
```

Bir diziden `CartesianIndices` oluşturmak, dizinin indekslerinin bir aralığını oluşturur.

!!! compat "Julia 1.6"
    Adım aralığı yöntemi `CartesianIndices((istart:istep:istop, jstart:[jstep:]jstop, ...))` en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> foreach(println, CartesianIndices((2, 2, 2)))
CartesianIndex(1, 1, 1)
CartesianIndex(2, 1, 1)
CartesianIndex(1, 2, 1)
CartesianIndex(2, 2, 1)
CartesianIndex(1, 1, 2)
CartesianIndex(2, 1, 2)
CartesianIndex(1, 2, 2)
CartesianIndex(2, 2, 2)

julia> CartesianIndices(fill(1, (2,3)))
CartesianIndices((2, 3))
```

## Doğrusal ve kartezyen indeksler arasında dönüşüm

Doğrusal indeksin kartezyen indekse dönüşümü, `CartesianIndices`'in bir `AbstractArray` olduğunu ve doğrusal olarak indekslenebileceğini kullanır:

```jldoctest
julia> cartesian = CartesianIndices((1:3, 1:2))
CartesianIndices((1:3, 1:2))

julia> cartesian[4]
CartesianIndex(1, 2)

julia> cartesian = CartesianIndices((1:2:5, 1:2))
CartesianIndices((1:2:5, 1:2))

julia> cartesian[2, 2]
CartesianIndex(3, 2)
```

## Yayılma

`CartesianIndices`, bir `CartesianIndex` ile yayılma aritmetiğini (+ ve -) destekler.

!!! compat "Julia 1.1"
    CartesianIndices'in yayılması en az Julia 1.1 gerektirir.


```jldoctest
julia> CIs = CartesianIndices((2:3, 5:6))
CartesianIndices((2:3, 5:6))

julia> CI = CartesianIndex(3, 4)
CartesianIndex(3, 4)

julia> CIs .+ CI
CartesianIndices((5:6, 9:10))
```

Kartezyen'den doğrusal indeks dönüşümü için, [`LinearIndices`](@ref) kısmına bakın. ```
