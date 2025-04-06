```
unsafe_read(io::IO, ref, nbytes::UInt)
```

Copie `nbytes` de l'objet de flux `IO` dans `ref` (converti en pointeur).

Il est recommandé que les sous-types `T<:IO` remplacent la signature de méthode suivante pour fournir des implémentations plus efficaces : `unsafe_read(s::T, p::Ptr{UInt8}, n::UInt)`
