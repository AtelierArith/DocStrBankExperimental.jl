```
digest!(context)
```

SHA bağlamını sonlandırın ve hash'i bayt dizisi (Array{Uint8, 1}) olarak döndürün. `digest!` çağrıldıktan sonra bağlamı güncellemek hata verecektir.

# Örnekler

```julia-repl
julia> ctx = SHA1_CTX()
SHA1 hash durumu

julia> update!(ctx, b"hash'lanacak veri")

julia> digest!(ctx)
20-element Array{UInt8,1}:
 0x83
 0xe4
 ⋮
 0x89
 0xf5

julia> update!(ctx, b"daha fazla veri")
HATA: `digest!` çağrıldıktan sonra CTX'i güncelleyemezsiniz
[...]
```
