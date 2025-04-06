```
Broadcast.broadcastable(x)
```

Ya `x` ya da `x` gibi bir nesne döndürür ki bu [`axes`](@ref), indeksleme destekler ve türü [`ndims`](@ref) destekler.

Eğer `x` yinelemeyi destekliyorsa, döndürülen değer [`collect(x)`](@ref) ile aynı `axes` ve indeksleme davranışlarına sahip olmalıdır.

Eğer `x` bir `AbstractArray` değilse ama `axes`, indeksleme destekliyorsa ve türü `ndims` destekliyorsa, o zaman `broadcastable(::typeof(x))` sadece kendisini döndürmek için uygulanabilir. Ayrıca, eğer `x` kendi [`BroadcastStyle`](@ref) tanımını yapıyorsa, o zaman özel stilin herhangi bir etkisi olması için `broadcastable` yöntemini kendisini döndürmek üzere tanımlamalıdır.

# Örnekler

```jldoctest
julia> Broadcast.broadcastable([1,2,3]) # diziler zaten axes ve indeksleme desteklediği için `identity` gibi
3-element Vector{Int64}:
 1
 2
 3

julia> Broadcast.broadcastable(Int) # Türler axes, indeksleme veya yineleme desteklemez ama genellikle skalar olarak kullanılır
Base.RefValue{Type{Int64}}(Int64)

julia> Broadcast.broadcastable("hello") # String'ler yineleme ile eşleşme kuralını bozar ve bunun yerine skalar gibi davranır
Base.RefValue{String}("hello")
```
