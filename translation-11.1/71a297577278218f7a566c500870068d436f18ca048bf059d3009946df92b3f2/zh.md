```
digest!(context)
```

最终化 SHA 上下文并返回哈希作为字节数组 (Array{Uint8, 1})。在调用 `digest!` 后更新上下文将会报错。

# 示例

```julia-repl
julia> ctx = SHA1_CTX()
SHA1 hash state

julia> update!(ctx, b"data to to be hashed")

julia> digest!(ctx)
20-element Array{UInt8,1}:
 0x83
 0xe4
 ⋮
 0x89
 0xf5

julia> update!(ctx, b"more data")
ERROR: Cannot update CTX after `digest!` has been called on it
[...]
```
