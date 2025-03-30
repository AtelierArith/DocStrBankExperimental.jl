```
bswap(n)
```

反转 `n` 的字节顺序。

（另见 [`ntoh`](@ref) 和 [`hton`](@ref) 以在当前本机字节顺序和大端字节顺序之间转换。）

# 示例

```jldoctest
julia> a = bswap(0x10203040)
0x40302010

julia> bswap(a)
0x10203040

julia> string(1, base = 2)
"1"

julia> string(bswap(1), base = 2)
"100000000000000000000000000000000000000000000000000000000"
```
