```
update!(context, data[, datalen])
```

Actualiza el contexto SHA con los bytes en data. Consulta también [`digest!`](@ref) para finalizar el hash.

# Ejemplos

```julia-repl
julia> ctx = SHA1_CTX()
Estado del hash SHA1

julia> update!(ctx, b"data to to be hashed")
```
