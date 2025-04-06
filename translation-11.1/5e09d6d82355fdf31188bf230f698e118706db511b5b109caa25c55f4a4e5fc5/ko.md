```
update!(context, data[, datalen])
```

SHA 컨텍스트를 데이터의 바이트로 업데이트합니다. 해시를 최종화하는 방법에 대해서는 [`digest!`](@ref)를 참조하세요.

# 예제

```julia-repl
julia> ctx = SHA1_CTX()
SHA1 해시 상태

julia> update!(ctx, b"해시할 데이터")
```
