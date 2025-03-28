```
cglobal((symbol, library) [, type=Cvoid])
```

Obtiene un puntero a una variable global en una biblioteca compartida exportada en C, especificada exactamente como en [`ccall`](@ref). Devuelve un `Ptr{Type}`, que por defecto es `Ptr{Cvoid}` si no se proporciona un argumento `Type`. Los valores se pueden leer o escribir mediante [`unsafe_load`](@ref) o [`unsafe_store!`](@ref), respectivamente.
