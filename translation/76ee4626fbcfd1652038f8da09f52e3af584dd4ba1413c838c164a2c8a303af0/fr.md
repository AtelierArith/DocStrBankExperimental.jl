```
mmap(io, BitArray, [dims, offset])
```

Créez un [`BitArray`](@ref) dont les valeurs sont liées à un fichier, en utilisant le mappage mémoire ; il a le même but, fonctionne de la même manière et a les mêmes arguments que [`mmap`](@ref mmap), mais la représentation en octets est différente.

# Exemples

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

Cela crée un `BitArray` de 25 par 30000, lié au fichier associé au flux `io`.
