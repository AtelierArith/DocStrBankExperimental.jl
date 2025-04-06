```
update!(context, data[, datalen])
```

使用数据中的字节更新SHA上下文。另请参见[`digest!`](@ref)以完成哈希。

# 示例

```julia-repl
julia> ctx = SHA1_CTX()
SHA1哈希状态

julia> update!(ctx, b"待哈希的数据")
```
