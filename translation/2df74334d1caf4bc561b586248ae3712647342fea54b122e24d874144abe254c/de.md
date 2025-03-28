```
cglobal((symbol, library) [, type=Cvoid])
```

Erhalten Sie einen Zeiger auf eine globale Variable in einer C-exportierten Shared Library, die genau wie in [`ccall`](@ref) angegeben ist. Gibt einen `Ptr{Type}` zurück, der standardmäßig auf `Ptr{Cvoid}` gesetzt ist, wenn kein `Type`-Argument angegeben ist. Die Werte können mit [`unsafe_load`](@ref) oder [`unsafe_store!`](@ref) gelesen oder geschrieben werden.
