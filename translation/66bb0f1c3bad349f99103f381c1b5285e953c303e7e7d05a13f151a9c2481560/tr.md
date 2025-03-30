```
convert(T, x)
```

`x`'i `T` türünde bir değere dönüştür.

Eğer `T` bir [`Integer`](@ref) türü ise, `x` `T` tarafından temsil edilemeyecekse, örneğin `x` tam sayı değeri değilse veya `T` tarafından desteklenen aralığın dışındaysa, bir [`InexactError`](@ref) hatası oluşacaktır.

# Örnekler

```jldoctest
julia> convert(Int, 3.0)
3

julia> convert(Int, 3.5)
HATA: InexactError: Int64(3.5)
Stacktrace:
[...]
```

Eğer `T` bir [`AbstractFloat`](@ref) türü ise, o zaman `T` tarafından temsil edilebilen `x`'e en yakın değeri döndürecektir. Inf, en yakın değeri belirlemek için `floatmax(T)`'den bir ulp daha büyük olarak kabul edilir.

```jldoctest
julia> x = 1/3
0.3333333333333333

julia> convert(Float32, x)
0.33333334f0

julia> convert(BigFloat, x)
0.333333333333333314829616256247390992939472198486328125
```

Eğer `T` bir koleksiyon türü ve `x` bir koleksiyon ise, `convert(T, x)`'in sonucu `x`'in tamamını veya bir kısmını aliaslayabilir.

```jldoctest
julia> x = Int[1, 2, 3];

julia> y = convert(Vector{Int}, x);

julia> y === x
true
```

Ayrıca bakınız: [`round`](@ref), [`trunc`](@ref), [`oftype`](@ref), [`reinterpret`](@ref).
