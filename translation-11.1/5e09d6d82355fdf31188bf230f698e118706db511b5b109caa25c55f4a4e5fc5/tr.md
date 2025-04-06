```
update!(context, data[, datalen])
```

SHA bağlamını verilerdeki baytlarla güncelleyin. Hash'i sonlandırmak için [`digest!`](@ref) ile de bakın.

# Örnekler

```julia-repl
julia> ctx = SHA1_CTX()
SHA1 hash durumu

julia> update!(ctx, b"hash'lanacak veri")
```
