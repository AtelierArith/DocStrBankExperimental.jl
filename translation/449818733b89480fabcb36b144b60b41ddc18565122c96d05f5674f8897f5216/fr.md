```
unsafe_write(io::IO, ref, nbytes::UInt)
```

Copie `nbytes` de `ref` (converti en pointeur) dans l'objet `IO`.

Il est recommandé que les sous-types `T<:IO` remplacent la signature de méthode suivante pour fournir des implémentations plus efficaces : `unsafe_write(s::T, p::Ptr{UInt8}, n::UInt)`
