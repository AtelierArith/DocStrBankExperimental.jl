```
eof(stream) -> Bool
```

Bir I/O akışının dosya sonuna ulaşıp ulaşmadığını test eder. Eğer akış henüz tükenmemişse, bu fonksiyon gerekli olduğunda daha fazla veri beklemek için bloklanacak ve ardından `false` döndürecektir. Bu nedenle, `eof`'un `false` döndüğünü gördükten sonra bir bayt okumak her zaman güvenlidir. `eof`, tamponlanmış veriler hala mevcut olduğu sürece `false` döndürecektir, bağlantının uzak ucu kapalı olsa bile.

# Örnekler

```jldoctest
julia> b = IOBuffer("my buffer");

julia> eof(b)
false

julia> seekend(b);

julia> eof(b)
true
```
