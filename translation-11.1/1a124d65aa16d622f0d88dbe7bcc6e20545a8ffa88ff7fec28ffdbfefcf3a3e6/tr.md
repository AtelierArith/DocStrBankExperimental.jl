```
reset(s::IO)
```

Bir akışı `s` daha önce işaretlenmiş bir konuma sıfırlayın ve işareti kaldırın. Daha önce işaretlenmiş konumu döndürün. Akış işaretlenmemişse bir hata fırlatın.

Ayrıca bkz. [`mark`](@ref), [`unmark`](@ref), [`ismarked`](@ref).
