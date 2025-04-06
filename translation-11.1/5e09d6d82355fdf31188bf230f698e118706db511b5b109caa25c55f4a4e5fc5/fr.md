```
update!(context, data[, datalen])
```

Met à jour le contexte SHA avec les octets dans les données. Voir aussi [`digest!`](@ref) pour finaliser le hachage.

# Exemples

```julia-repl
julia> ctx = SHA1_CTX()
État de hachage SHA1

julia> update!(ctx, b"data to to be hashed")
```
