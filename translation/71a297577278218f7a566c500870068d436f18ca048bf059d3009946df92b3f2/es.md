```
digest!(context)
```

Finaliza el contexto SHA y devuelve el hash como un array de bytes (Array{Uint8, 1}). Actualizar el contexto después de llamar a `digest!` en él generará un error.

# Ejemplos

```julia-repl
julia> ctx = SHA1_CTX()
Estado del hash SHA1

julia> update!(ctx, b"datos a ser hasheados")

julia> digest!(ctx)
Array{UInt8,1} de 20 elementos:
 0x83
 0xe4
 ⋮
 0x89
 0xf5

julia> update!(ctx, b"más datos")
ERROR: No se puede actualizar CTX después de que se haya llamado a `digest!` en él
[...]
```
