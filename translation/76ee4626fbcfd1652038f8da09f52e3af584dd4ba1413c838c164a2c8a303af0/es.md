```
mmap(io, BitArray, [dims, offset])
```

Crea un [`BitArray`](@ref) cuyos valores están vinculados a un archivo, utilizando mapeo de memoria; tiene el mismo propósito, funciona de la misma manera y tiene los mismos argumentos que [`mmap`](@ref mmap), pero la representación en bytes es diferente.

# Ejemplos

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

Esto crea un `BitArray` de 25 por 30000, vinculado al archivo asociado con el flujo `io`.
