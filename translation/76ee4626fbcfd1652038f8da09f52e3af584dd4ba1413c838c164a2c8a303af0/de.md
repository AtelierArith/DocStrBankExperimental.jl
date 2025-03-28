```
mmap(io, BitArray, [dims, offset])
```

Erstellt ein [`BitArray`](@ref), dessen Werte mit einer Datei verknüpft sind, indem es eine Speicherabbildung verwendet; es hat denselben Zweck, funktioniert auf die gleiche Weise und hat dieselben Argumente wie [`mmap`](@ref mmap), aber die Byte-Darstellung ist anders.

# Beispiele

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

Dies erstellt ein 25-mal-30000 `BitArray`, das mit der Datei verknüpft ist, die mit dem Stream `io` assoziiert ist.
