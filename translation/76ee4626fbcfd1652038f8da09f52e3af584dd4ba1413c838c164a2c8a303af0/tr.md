```
mmap(io, BitArray, [dims, offset])
```

Bir dosyaya bağlı değerleri olan bir [`BitArray`](@ref) oluşturur, bellek eşlemesi kullanarak; aynı amaca sahiptir, aynı şekilde çalışır ve [`mmap`](@ref mmap) ile aynı argümanlara sahiptir, ancak bayt temsili farklıdır.

# Örnekler

```jldoctest
julia> using Mmap

julia> io = open("mmap.bin", "w+");

julia> B = mmap(io, BitArray, (25,30000));

julia> B[3, 4000] = true;

julia> Mmap.sync!(B);

julia> close(io);

julia> io = open("mmap.bin", "r+");

julia> C = mmap(io, BitArray, (25,30000));

julia> C[3, 4000]
true

julia> C[2, 4000]
false

julia> close(io)

julia> rm("mmap.bin")
```

Bu, `io` akışıyla ilişkili dosyaya bağlı 25'e 30000 boyutunda bir `BitArray` oluşturur.
