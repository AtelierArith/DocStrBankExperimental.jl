```
digest!(context)
```

SHA 컨텍스트를 최종화하고 해시를 바이트 배열(Array{Uint8, 1})로 반환합니다. `digest!`를 호출한 후에 컨텍스트를 업데이트하면 오류가 발생합니다.

# 예제

```julia-repl
julia> ctx = SHA1_CTX()
SHA1 해시 상태

julia> update!(ctx, b"해시할 데이터")

julia> digest!(ctx)
20-element Array{UInt8,1}:
 0x83
 0xe4
 ⋮
 0x89
 0xf5

julia> update!(ctx, b"추가 데이터")
ERROR: `digest!`가 호출된 후 CTX를 업데이트할 수 없습니다
[...]
```
