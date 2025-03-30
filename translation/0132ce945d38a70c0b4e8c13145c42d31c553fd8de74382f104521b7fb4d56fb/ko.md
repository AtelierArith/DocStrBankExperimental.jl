```
bswap(n)
```

`n`의 바이트 순서를 반전시킵니다.

(현재 네이티브 바이트 순서와 빅 엔디안 순서 간의 변환을 위해 [`ntoh`](@ref) 및 [`hton`](@ref)를 참조하십시오.)

# 예제

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
